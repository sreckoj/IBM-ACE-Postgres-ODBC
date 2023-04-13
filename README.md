
# Connecting from IBM App Connect Enterprise to PostgreSQL using ODBC on Linux

The example described in this blog was tested on CentOS 8. Similar steps can be performed on other Linux distributions. All commands are executed with root or postgres user identity.

## Install PostgreSQL

Go to https://postgresql.org. Click **Download**, select your Linux distribution, and provide version and platform details to generate the installation commands. The following commands were used in the described example:

Install package:
```sh
dnf install -y https://download.postgresql.org/pub/repos/yum/reporpms/EL-8-x86_64/pgdg-redhat-repo-latest.noarch.rpm
```

Disable the default module that comes with Linux (usually not the latest version):
```sh
dnf -qy module disable postgresql
```

Install Postgres server (version 15 in this case):
```sh
dnf install -y postgresql15-server
```

Run the initial setup. Enable and start the service:
```sh
/usr/pgsql-15/bin/postgresql-15-setup initdb
systemctl enable postgresql-15
systemctl start postgresql-15
```

Install additional libraries required for ODBC:
```sh
dnf install -y postgresql15-contrib
dnf install -y postgresql15-odbc
```

Set the password for the postgres user (automatically created during installation):
```sh
passwd postgres
```

## Create a sample database table



























