---
title: "Problem starting MySQL on VPS running Ubuntu Server"
date: 2008-12-04
forum: Server Platforms
---

### Post by ZTecWiz on 2008-12-04
#
Dec  4 09:41:05 server mysqld_safe[6034]: started
#
Dec  4 09:41:06 server mysqld[6038]: InnoDB: The first specified data file ./ibdata1 did not exist:
#
Dec  4 09:41:06 server mysqld[6038]: InnoDB: a new database to be created!
#
Dec  4 09:41:06 server mysqld[6038]: 081204  9:41:06  InnoDB: Setting file ./ibdata1 size to 10 MB
#
Dec  4 09:41:06 server mysqld[6038]: InnoDB: Database physically writes the file full: wait...
#
Dec  4 09:41:06 server mysqld[6038]: 081204  9:41:06  InnoDB: Log file ./ib_logfile0 did not exist: new to be created
#
Dec  4 09:41:06 server mysqld[6038]: InnoDB: Setting log file ./ib_logfile0 size to 5 MB
#
Dec  4 09:41:06 server mysqld[6038]: InnoDB: Database physically writes the file full: wait...
#
Dec  4 09:41:06 server mysqld[6038]: 081204  9:41:06  InnoDB: Log file ./ib_logfile1 did not exist: new to be created
#
Dec  4 09:41:06 server mysqld[6038]: InnoDB: Setting log file ./ib_logfile1 size to 5 MB
#
Dec  4 09:41:06 server mysqld[6038]: InnoDB: Database physically writes the file full: wait...
#
Dec  4 09:41:06 server mysqld[6038]: InnoDB: Error: pthread_create returned 12
#
Dec  4 09:41:06 server mysqld_safe[6044]: ended
#
Dec  4 09:41:20 server /etc/init.d/mysql[7228]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
#
Dec  4 09:41:20 server /etc/init.d/mysql[7228]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
#
Dec  4 09:41:20 server /etc/init.d/mysql[7228]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
#
Dec  4 09:41:20 server /etc/init.d/mysql[7228]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
#
Dec  4 09:41:20 server /etc/init.d/mysql[7228]:
#
root@server:/#


Those are the errors I get in syslog after this:

root@server:/# /etc/init.d/mysql start
 * Starting MySQL database server mysqld
   ...fail!
root@server:/#


When I install 'mysql-server-5.0' package:

Selecting previously deselected package mysql-server-5.0.
(Reading database ... 15001 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.51a-3ubuntu5.4_i386.deb) ...
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.4) ...
 * Stopping MySQL database server mysqld
   ...done.
 * Starting MySQL database server mysqld
   ...fail!
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@server:/#

---

