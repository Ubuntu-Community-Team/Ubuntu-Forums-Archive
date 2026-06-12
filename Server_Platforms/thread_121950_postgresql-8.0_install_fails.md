---
title: "postgresql-8.0 install fails"
date: 2006-01-26
forum: Server Platforms
---

### Post by lerouxb on 2006-01-26
Hi. I tried to install postgresql-8.0, but got the error listed below. I removed it and tried again, but I keep getting the same error. Any ideas?

```
leroux@lapdog:~$ sudo apt-get install postgresql-8.0 postgresql-client-8.0
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  postgresql-common
The following NEW packages will be installed:
  postgresql-8.0 postgresql-client-8.0 postgresql-common
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3415kB of archives.
After unpacking 16.7MB of additional disk space will be used.
Do you want to continue [Y/n]? Y

Preconfiguring packages ...
Selecting previously deselected package postgresql-common.
(Reading database ... 89846 files and directories currently installed.)
Unpacking postgresql-common (from .../postgresql-common_27ubuntu1_all.deb) ...
Selecting previously deselected package postgresql-client-8.0.
Unpacking postgresql-client-8.0 (from .../postgresql-client-8.0_8.0.3-15ubuntu2_i386.deb) ...
Selecting previously deselected package postgresql-8.0.
Unpacking postgresql-8.0 (from .../postgresql-8.0_8.0.3-15ubuntu2_i386.deb) ...
Setting up postgresql-common (27ubuntu1) ...
 * Stopping PostgreSQL 8.0 database server: main Error: cluster is not running
                                                                         [fail]
 * Starting PostgreSQL 8.0 database server: main pg_controldata: could not open file "/var/lib/postgresql/8.0/main/global/pg_control" for reading: No such file or directory
Error: Could not parse locale out of pg_controldata output
                                                                         [fail]

Setting up postgresql-client-8.0 (8.0.3-15ubuntu2) ...

Setting up postgresql-8.0 (8.0.3-15ubuntu2) ...
 * Starting PostgreSQL 8.0 database server: main pg_controldata: could not open file "/var/lib/postgresql/8.0/main/global/pg_control" for reading: No such file or directory
Error: Could not parse locale out of pg_controldata output
                                                                         [fail]
```

---

### Post by lerouxb on 2006-01-26
nevermind. I did a
rm /etc/postgresql-common/postgresql.pem
rm -rf /var/lib/postgresql

and now it installs fine. weird.

---

