---
title: "mysql_config / MySQL dev stuff in intrepid?"
date: 2009-02-11
forum: Server Platforms
---

### Post by clauslund on 2009-02-11
I'm trying to compile Zabbix from source with a MySQL backend ... what package(s) do I need to install to get the MySQL development stuff?

[FONT="Courier New"]clund@log-server:~$ dpkg -l '*'|grep -i mysql
ii  libdbd-mysql-perl                 4.007-1build1                 A Perl5 database interface to the MySQL data
un  libmysqlclient15                  <none>                        (no description available)
ii  libmysqlclient15off               5.0.67-0ubuntu6               MySQL database client library
un  mysql-client                      <none>                        (no description available)
ii  mysql-client-5.0                  5.0.67-0ubuntu6               MySQL database client binaries
ii  mysql-common                      5.0.67-0ubuntu6               MySQL database common files
un  mysql-community-client-5.0        <none>                        (no description available)
un  mysql-community-server-5.0        <none>                        (no description available)
un  mysql-doc-5.0                     <none>                        (no description available)
un  mysql-enterprise-client-5.0       <none>                        (no description available)
un  mysql-enterprise-server-5.0       <none>                        (no description available)
ii  mysql-server                      5.0.67-0ubuntu6               MySQL database server (metapackage depending
ii  mysql-server-5.0                  5.0.67-0ubuntu6               MySQL database server binaries
un  php4-mysql                        <none>                        (no description available)
ii  php5-mysql                        5.2.6-2ubuntu4                MySQL module for php5
un  php5-mysqli                       <none>                        (no description available)
un  virtual-mysql-client              <none>                        (no description available)
un  virtual-mysql-server              <none>                        (no description available)
rc  zabbix-server-mysql               1:1.4.6-1ubuntu1              software for monitoring of your networks --
[/FONT]

---

### Post by cdenley on 2009-02-11
```

sudo apt-get build-dep zabbix-server-mysql

```

---

