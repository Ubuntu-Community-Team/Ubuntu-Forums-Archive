---
title: "server 8.10 - problem with mysql installation"
date: 2008-12-27
forum: Server Platforms
---

### Post by poilkjq on 2008-12-27
Hi
when I'm installing mysql server (5) on my ubuntu server 8.10, still I get this problem:
(used this install tutorial [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts) -> same as 8.10), many thanks

bruno@peki314:~$ sudo apt-get install mysql-server mysql-client
[sudo] password for bruno:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libdbd-mysql-perl libmysqlclient15off mysql-client-5.0 mysql-common
  mysql-server-5.0
Suggested packages:
  mysql-doc-5.0 tinyca mailx
The following NEW packages will be installed:
  libdbd-mysql-perl libmysqlclient15off mysql-client mysql-client-5.0
  mysql-common mysql-server mysql-server-5.0
0 upgraded, 7 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/36.9MB of archives.
After this operation, 111MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package mysql-common.
(Reading database ... 26168 files and directories currently installed.)
Unpacking mysql-common (from .../mysql-common_5.0.67-0ubuntu6_all.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from .../libmysqlclient15off_5.0.67-0ubuntu6_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.007-1build1_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.67-0ubuntu6_i386.deb) ...
Processing triggers for man-db ...
Setting up mysql-common (5.0.67-0ubuntu6) ...
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 26280 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.67-0ubuntu6_i386.deb) ...
Selecting previously deselected package mysql-client.
Unpacking mysql-client (from .../mysql-client_5.0.67-0ubuntu6_all.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.67-0ubuntu6_all.deb) ...
Processing triggers for man-db ...
Setting up libmysqlclient15off (5.0.67-0ubuntu6) ...

Setting up libdbd-mysql-perl (4.007-1build1) ...
Setting up mysql-client-5.0 (5.0.67-0ubuntu6) ...
Setting up mysql-server-5.0 (5.0.67-0ubuntu6) ...
 * Stopping MySQL database server mysqld                                 [ OK ]
ERROR: 1146  Table 'mysql.user' doesn't exist
081227  1:33:56 [ERROR] Aborting

081227  1:33:56 [Note] /usr/sbin/mysqld: Shutdown complete

 * Starting MySQL database server mysqld                                 [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up mysql-client (5.0.67-0ubuntu6) ...
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by spiderbatdad on 2008-12-27
Not totally sure, but I believe you just need to go ahead and create a databse...at least one entry, and a users table, then restart mysql. Maybe these steps are later in your tutorial? Usually mysql has to be configured by creating a user and password.```
mysqladmin -u root password your_password 
```where your_password is something you make up.
Then login with ```
mysql -u root -p
create database dbname;
exit; 
```and so forth. restart the server: ```
sudo /etc/init.d/mysql restart
```
Do you really need mysql? What are you goals for installing a server?

---

### Post by poilkjq on 2008-12-27
> **spiderbatdad said:**
> Not totally sure, but I believe you just need to go ahead and create a databse...at least one entry, and a users table, then restart mysql. Maybe these steps are later in your tutorial? Usually mysql has to be configured by creating a user and password.```
mysqladmin -u root password your_password 
```where your_password is something you make up.
Then login with ```
mysql -u root -p
create database dbname;
exit; 
```and so forth. restart the server: ```
sudo /etc/init.d/mysql restart
```

cant connect, mysql server isn't running

---

### Post by spiderbatdad on 2008-12-27
maybe try:```
sudo apt-get remove --purge mysql-server mysql-client && sudo apt-get install mysql-client mysql-server
```On question might be, why install a server on 8.10 which is part of a six month release development cycle? 8.04 is much more suited to your purpose, as a LTS release...so I'm sorry I have not tried installing these packages on Intrepid.

You should be prompted for a password during the installation.

---

### Post by cariboo on 2008-12-27
I would suggest just installing the mysql-server:

```
sudo apt-get install mysql-server-5.0
```

apt will take care of installing the dependencies. I would also suggest installing the mysql-doc package.

Jim

---

