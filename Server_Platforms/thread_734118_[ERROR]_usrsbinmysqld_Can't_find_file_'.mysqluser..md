---
title: "[ERROR] /usr/sbin/mysqld: Can't find file: './mysql/user.frm'"
date: 2008-03-24
forum: Server Platforms
---

### Post by syn4k on 2008-03-24
ray@ray-desktop:/etc/mysql$ **sudo apt-get autoremove --purge mysql-server mysql-server-5.0**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mysql-server* mysql-server-5.0*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 84.6MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 117355 files and directories currently installed.)
Removing mysql-server ...
Removing mysql-server-5.0 ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Purging configuration files for mysql-server-5.0 ...
ray@ray-desktop:/etc/mysql$ **sudo apt-get install mysql-server mysql-client-5.0**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-client-5.0 is already the newest version.
The following extra packages will be installed:
  mysql-server-5.0
Suggested packages:
  tinyca mysql-doc-5.0
Recommended packages:
  mailx
The following NEW packages will be installed:
  mysql-server mysql-server-5.0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/26.8MB of archives.
After unpacking 84.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 115436 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.45-1ubuntu3.3_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.45-1ubuntu3.3_all.deb) ...
Setting up mysql-server-5.0 (5.0.45-1ubuntu3.3) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
[B]080324 11:06:56 [ERROR] /usr/sbin/mysqld: Can't find file: './mysql/user.frm' (errno: 13)
080324 11:06:56 [ERROR] /usr/sbin/mysqld: Can't find file: './mysql/user.frm' (errno: 13)
ERROR: 1017  Can't find file: './mysql/user.frm' (errno: 13)
080324 11:06:56 [ERROR] Aborting[/B]

080324 11:06:56 [Note] /usr/sbin/mysqld: Shutdown complete

 [B]* /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
grep: /etc/mysql/my.cnf: No such file or directory[/B]
 * Starting MySQL database server mysqld                                 [fail] 
**invoke-rc.d: initscript mysql, action "start" failed.**
[B]dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status [/B]1
dpkg: dependency problems prevent configuration of mysql-server:
 **mysql-server depends on mysql-server-5.0; however:**
  **Package mysql-server-5.0 is not configured yet.**
dpkg: error processing mysql-server (--configure):
 [B]dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]
ray@ray-desktop:/etc/mysql$

---

