---
title: "MySQL Server Problems"
date: 2011-07-30
forum: Server Platforms
---

### Post by dmubu on 2011-07-30
I have been trying to get MySQL to work within the LAMP stack, but have been unsuccessful.

I used tasksel to install, per the recommendation.

After the install, I run mysql and receive:

```

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

I looked in my file system, and it turns out that the mysqld directory is blank.  What should I do?  I have already tried reinstalling twice.

---

### Post by fdrake on 2011-07-30
you can try to install it thought the repo.
```
sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql
```

---

### Post by dmubu on 2011-07-30
Here is what I ran with the result:

```

sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdbd-mysql-perl libmysqlclient16 mysql-client-5.1 mysql-client-core-5.1
  mysql-common mysql-server-5.1 mysql-server-core-5.1
Suggested packages:
  tinyca
The following NEW packages will be installed:
  libapache2-mod-auth-mysql libdbd-mysql-perl libmysqlclient16
  mysql-client-5.1 mysql-client-core-5.1 mysql-common mysql-server
  mysql-server-5.1 mysql-server-core-5.1 php5-mysql
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/21.7 MB of archives.
After this operation, 51.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
Selecting previously deselected package mysql-common.
(Reading database ... 165813 files and directories currently installed.)
Unpacking mysql-common (from .../mysql-common_5.1.54-1ubuntu4_all.deb) ...
Selecting previously deselected package libmysqlclient16.
Unpacking libmysqlclient16 (from .../libmysqlclient16_5.1.54-1ubuntu4_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.016-1_i386.deb) ...
Selecting previously deselected package mysql-client-core-5.1.
Unpacking mysql-client-core-5.1 (from .../mysql-client-core-5.1_5.1.54-1ubuntu4_i386.deb) ...
Selecting previously deselected package mysql-client-5.1.
Unpacking mysql-client-5.1 (from .../mysql-client-5.1_5.1.54-1ubuntu4_i386.deb) ...
Selecting previously deselected package mysql-server-core-5.1.
Unpacking mysql-server-core-5.1 (from .../mysql-server-core-5.1_5.1.54-1ubuntu4_i386.deb) ...
Processing triggers for man-db ...
Setting up mysql-common (5.1.54-1ubuntu4) ...
Selecting previously deselected package mysql-server-5.1.
(Reading database ... 166010 files and directories currently installed.)
Unpacking mysql-server-5.1 (from .../mysql-server-5.1_5.1.54-1ubuntu4_i386.deb) ...
Selecting previously deselected package libapache2-mod-auth-mysql.
Unpacking libapache2-mod-auth-mysql (from .../libapache2-mod-auth-mysql_4.3.9-13ubuntu1_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.1.54-1ubuntu4_all.deb) ...
Selecting previously deselected package php5-mysql.
Unpacking php5-mysql (from .../php5-mysql_5.3.5-1ubuntu7.2_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for libapache2-mod-php5 ...
 * Reloading web server config apache2                                   [ OK ] 
Setting up libmysqlclient16 (5.1.54-1ubuntu4) ...
Setting up libdbd-mysql-perl (4.016-1) ...
Setting up mysql-client-core-5.1 (5.1.54-1ubuntu4) ...
Setting up mysql-client-5.1 (5.1.54-1ubuntu4) ...
Setting up mysql-server-core-5.1 (5.1.54-1ubuntu4) ...
Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
mysql start/running, process 400
Setting up libapache2-mod-auth-mysql (4.3.9-13ubuntu1) ...
Setting up mysql-server (5.1.54-1ubuntu4) ...
Setting up php5-mysql (5.3.5-1ubuntu7.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


```

I ran mysql again.
```

mysql

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


```

Next, I tried:
```
sudo service mysql stop
mysql stop/waiting

```

And then:

```

mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

Any other suggestions????

---

### Post by brighty22 on 2011-07-30
It could be caused by a thousand things. This works for some:

```
sudo chmod 775 /var/lib/mysql
```

Then start mysql and try connecting with a username, ie.

```
mysql -u root -p
```

---

