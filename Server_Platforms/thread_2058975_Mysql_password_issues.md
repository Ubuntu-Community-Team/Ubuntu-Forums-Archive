---
title: "Mysql password issues"
date: 2012-09-17
forum: Server Platforms
---

### Post by felinoel on 2012-09-17
The password I set up for it appears to not be working, how would I go about resetting this?


EDIT:
Actually, I am not even sure if the database was actually set up too... I could have sworn it was, but it seems like it isn't based on password changing I've tried.

---

### Post by jaithehulk on 2012-09-17
Even I have a question related to this..I did not setup a pwd while installing MySql.. now I want to set a pwd.. how do i do this?
I did not want to raise a new thread. so posting it here...

---

### Post by Habitual on 2012-09-17
```
sudo apt-get install -y debconf-utils
debconf-get-selections | grep mysql | grep password

```

to "see" the password used to install mysql.

---

### Post by youngunix on 2012-09-17
> **Habitual said:**
> ```
sudo apt-get install -y debconf-utils
debconf-get-selections | grep mysql | grep password

```to "see" the password used to install mysql.

I am using lampp, and when I tried the above method, I get nothing!

---

### Post by felinoel on 2012-09-17
> **Habitual said:**
> ```
sudo apt-get install -y debconf-utils
debconf-get-selections | grep mysql | grep password

```

to "see" the password used to install mysql.

```
me@3MJ:~$ debconf-get-selections | grep mysql | grep password
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
mysql-server-5.5	mysql-server/error_setting_password	error	
mysql-server-5.5	mysql-server/password_mismatch	error	
me@3MJ:~$ 

```

---

### Post by Habitual on 2012-09-17
```
sudo debconf-get-selections | grep mysql | grep password
```
then. :)

---

### Post by youngunix on 2012-09-17
> **Habitual said:**
> ```
sudo debconf-get-selections | grep mysql | grep password
```then. :)

:lolflag:
I tried that first, then without superuser privileges and still get nothing. No beggie though, I was just wondering.

---

### Post by sandyd on 2012-09-17
> **felinoel said:**
> The password I set up for it appears to not be working, how would I go about resetting this?


EDIT:
Actually, I am not even sure if the database was actually set up too... I could have sworn it was, but it seems like it isn't based on password changing I've tried.
Quick crash course.

**List Databases:**
```

SHOW DATABASES;

```
[B]
Drop (Delete) Database:[/B]
```

DROP DATABASE **database_name**

```

**List Users:**
```

SELECT user FROM mysql.user;

```

**Drop User:**
```

DROP USER **your_username**

```
If you created the username with the @, i.e. 'your_username'@'localhost', you will have to use the same thing to drop the user.

i.e.
```

DROP USER [b]'your_username'@'localhost'
```

Now, to create a new database and assign a user to it...
Login to mysql.
```

CREATE DATABASE your_database_name;
GRANT ALL ON your_database_name.* TO your_username IDENTIFIED BY 'your_password'

```
and yes, replace your_database_name, your_username, and your_password.

You might want to do ```
 'your_username'@'localhost'
``` depending if the server is local or not.

---

### Post by felinoel on 2012-09-17
> **Habitual said:**
> ```
sudo debconf-get-selections | grep mysql | grep password
```
then. :)

Tried that directly after without, same response.

> **sandyd said:**
> Quick crash course.

**List Databases:**
```

SHOW DATABASES;

```
[B]
Drop (Delete) Database:[/B]
```

DROP DATABASE **database_name**

```

**List Users:**
```

SELECT user FROM mysql.user;

```

**Drop User:**
```

DROP USER **your_username**

```
If you created the username with the @, i.e. 'your_username'@'localhost', you will have to use the same thing to drop the user.

i.e.
```

DROP USER [b]'your_username'@'localhost'
```

Now, to create a new database and assign a user to it...
Login to mysql.
```

CREATE DATABASE your_database_name;
GRANT ALL ON your_database_name.* TO your_username IDENTIFIED BY 'your_password'

```
and yes, replace your_database_name, your_username, and your_password.

You might want to do ```
 'your_username'@'localhost'
``` depending if the server is local or not.Could you crash a little harder?

```
me@3MJ:~$ SHOW DATABASES:
SHOW: command not found
me@3MJ:~$
```

EDIT:
Oh do I need to be in mysql when I do that command?

EDIT:
```
me@3MJ:~$ sudo mysql
[sudo] password for me: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
me@3MJ:~$ 
```
I forgot how to get into mysql...

---

### Post by sandyd on 2012-09-18
should be
```

mysql -uroot -p

```
and enter your mysql root password

---

### Post by felinoel on 2012-09-18
> **sandyd said:**
> should be
```

mysql -u root -p

```
and enter your mysql root password
Already tried that but it asked for my mysql root password when I do that.

---

### Post by sandyd on 2012-09-18
oh, you don't know your mysql password?

That cant be good.

```

dpkg-reconfigure mysql-server-5.5
```

---

### Post by felinoel on 2012-09-18
> **sandyd said:**
> oh, you don't know your mysql password?

That cant be good.

```

dpkg-reconfigure mysql-server-5.5
```I don't remember setting one up, isn't that what the title of this thread and the OP says?

---

### Post by felinoel on 2012-09-18
> **sandyd said:**
> ```
dpkg-reconfigure mysql-server-5.5
```
Ok so I did all that...```
me@3MJ:~$ sudo dpkg-reconfigure mysql-server-5.5
[sudo] password for me: 
mysql stop/waiting
120918 17:13:32 [Note] Plugin 'FEDERATED' is disabled.
120918 17:13:32 InnoDB: The InnoDB memory heap is disabled
120918 17:13:32 InnoDB: Mutexes and rw_locks use GCC atomic builtins
120918 17:13:32 InnoDB: Compressed tables use zlib 1.2.3.4
120918 17:13:32 InnoDB: Initializing buffer pool, size = 128.0M
120918 17:13:32 InnoDB: Completed initialization of buffer pool
120918 17:13:32 InnoDB: highest supported file format is Barracuda.
120918 17:13:32  InnoDB: Waiting for the background threads to start
120918 17:13:33 InnoDB: 1.1.8 started; log sequence number 3307488
120918 17:13:33  InnoDB: Starting shutdown...
120918 17:13:34  InnoDB: Shutdown completed; log sequence number 3307488
mysql start/running, process 15304
``` but then...```

me@3MJ:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
me@3MJ:~$ 
```I KNOW I put in the password I just changed it to..?

---

### Post by sandyd on 2012-09-18
Try
```

sudo dpkg-reconfigure mysql-server

```
instead

---

### Post by felinoel on 2012-09-19
> **sandyd said:**
> Try
```

sudo dpkg-reconfigure mysql-server

```
instead

```
me@3MJ:~$ sudo dpkg-reconfigure mysql-server
[sudo] password for me: 
me@3MJ:~$ 
``````

me@3MJ:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
me@3MJ:~$ 

```

---

### Post by felinoel on 2012-09-19
Someone linked me to [this guide](http://wiki.vpslink.com/Change_MySQL_root_Password) which didn't work, if it helps see this.

```
me@3MJ:~$ sudo /etc/init.d/mysql stop
[sudo] password for me: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mysql
mysql stop/waiting
me@3MJ:~$ mysqld_safe --skip-grant-tables --skip networking &
[1] 21978
me@3MJ:~$ 120919 23:12:33 mysqld_safe Logging to syslog.
120919 23:12:33 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
120919 23:12:33 mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended
mysql mysql -uroot
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
[1]+  Done                    mysqld_safe --skip-grant-tables --skip networking
me@3MJ:~$ 
me@3MJ:~$ 
me@3MJ:~$ mysqladmin -u root password ""
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
me@3MJ:~$ mysql start
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
me@3MJ:~$ 

```

---

### Post by cariboo on 2012-09-20
I'm using the 12.04  server install here, in order to set the mysql password, which is different from the root password, first you have to determine what version of mysql you are using. In my case it's mysql-server-5.5.

To determins what version you are using, if you don't know, at the prompt type:

```
sudo apt-cache showpkg mysql-server
```

You may have to pipe the output to a text file, as the output on my system doesn't fit in a terminal screen.

Once you have determined what version you are using type (in my example I use mysql-server-5.5):

```
sudo dpkg-reconfigure mysql-server-5.5
```

You should next see something similar to the screenshot.

Remember, the root mysql user, is not the same as your computer root user, use a different password, if you have enabled the root account.

---

### Post by felinoel on 2012-09-20
> **cariboo907 said:**
> 
Did all that, but it still won't let me log in.
```
me@3MJ:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
me@3MJ:~$ 

```

---

### Post by Habitual on 2012-09-20
If I knew the command of the top-of-my-head, I'd give it to you, but a *purge* of mysql-server may be in order.

someone will chime in with the command to do that, sorry.

---

### Post by felinoel on 2012-09-20
> **Habitual said:**
> If I knew the command of the top-of-my-head, I'd give it to you, but a *purge* of mysql-server may be in order.

someone will chime in with the command to do that, sorry.

What if I just reinstalled Ubuntu?

---

### Post by Habitual on 2012-09-20
> **felinoel said:**
> What if I just reinstalled Ubuntu?

Is that the conclusion you arrived at? Re-install? All I can say to that is "Even a broke watch is right twice a day". 

How about you don't? Seriously.
Re-installing the OS is the *last* resort and it doesn't fix anything and you never learn how to fix things by doing so. 

Having said that, check [this]("https://help.ubuntu.com/community/AptGet/Howto#Removal_commands")
and bookmark this: [CommandLineResources]("https://help.ubuntu.com/community/CommandLineResources")

Please don't reinstall the OS, it is a fixable issue.

---

### Post by felinoel on 2012-09-20
> **Habitual said:**
> Is that the conclusion you arrived at? Re-install? All I can say to that is "Even a broke watch is right twice a day". 

How about you don't? Seriously.
Re-installing the OS is the *last* resort and it doesn't fix anything and you never learn how to fix things by doing so. 

Having said that, check [this]("https://help.ubuntu.com/community/AptGet/Howto#Removal_commands")
and bookmark this: [CommandLineResources]("https://help.ubuntu.com/community/CommandLineResources")

Please don't reinstall the OS, it is a fixable issue.```
me@3MJ:~$ apt-get remove mysql
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
me@3MJ:~$ sudo apt-get remove mysql
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mysql
me@3MJ:~$ sudo apt-get purge mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mysql
me@3MJ:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 libtotem0 totem-common
0 upgraded, 0 newly installed, 4 to remove and 14 not upgraded.
After this operation, 2,816 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 154256 files and directories currently installed.)
Removing gir1.2-totem-1.0 ...
Removing gir1.2-totem-plparser-1.0 ...
Removing libtotem0 ...
Removing totem-common ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for libglib2.0-0 ...
Processing triggers for gconf2 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
me@3MJ:~$ 

```Ok I even did the autoremove to get rid of the extra bits... so then if the guide I followed was apparently outdated I am guessing (since this issue came), what should I do to set up a database for a phpbb3 message board?

---

### Post by Habitual on 2012-09-21
Now, re-install mysql-server and pay close attention to the dialogs.
```
sudo apt-get install mysql-server
```

---

### Post by felinoel on 2012-09-21
> **Habitual said:**
> Now, re-install mysql-server and pay close attention to the dialogs.
```
sudo apt-get install mysql-server
```

```
me@3MJ:~$ sudo apt-get install mysql-server
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
me@3MJ:~$ 

```Efff wtf!? Why is this still not removed... x.x
I am really tempted to just reinstall...

---

### Post by Habitual on 2012-09-22
Did you ***purge*** mysql-server?

---

### Post by felinoel on 2012-09-22
> **Habitual said:**
> Did you ***purge*** mysql-server?

> **felinoel said:**
> ```
me@3MJ:~$ apt-get remove mysql
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
me@3MJ:~$ sudo apt-get remove mysql
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mysql
me@3MJ:~$ sudo apt-get purge mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mysql
me@3MJ:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 libtotem0 totem-common
0 upgraded, 0 newly installed, 4 to remove and 14 not upgraded.
After this operation, 2,816 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 154256 files and directories currently installed.)
Removing gir1.2-totem-1.0 ...
Removing gir1.2-totem-plparser-1.0 ...
Removing libtotem0 ...
Removing totem-common ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for libglib2.0-0 ...
Processing triggers for gconf2 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
me@3MJ:~$ 

```Ok I even did the autoremove to get rid of the extra bits... so then if the guide I followed was apparently outdated I am guessing (since this issue came), what should I do to set up a database for a phpbb3 message board?
Yes.

---

### Post by steeldriver on 2012-09-22
... I'm not sure you did...

> 
```
me@3MJ:~$ [COLOR=Red][COLOR=black]sudo apt-get remove [/COLOR]**mysql**[/COLOR]
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=Red]**E: Unable to locate package mysql**[/COLOR]
me@3MJ:~$ [COLOR=Red][COLOR=black]sudo apt-get purge[/COLOR]** mysql**[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=Red]**E: Unable to locate package mysql**[/COLOR]
me@3MJ:~$ [COLOR=Red][COLOR=black]sudo apt-get [/COLOR]**autoremove**[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=Red][B]The following packages will be REMOVED:
  gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 libtotem0 totem-common[/B][/COLOR]
```Try

```
sudo apt-get purge **mysql-server**
```

---

### Post by felinoel on 2012-09-22
> **steeldriver said:**
> ... I'm not sure you did...

Try

```
sudo apt-get purge **mysql-server**
```

```
me@3MJ:~$ sudo apt-get purge mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mysql-server*
0 upgraded, 0 newly installed, 1 to remove and 29 not upgraded.
After this operation, 115 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 158222 files and directories currently installed.)
Removing mysql-server ...
me@3MJ:~$ 
me@3MJ:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mysql-server
0 upgraded, 1 newly installed, 0 to remove and 29 not upgraded.
Need to get 0 B/11.7 kB of archives.
After this operation, 115 kB of additional disk space will be used.
Selecting previously unselected package mysql-server.
(Reading database ... 158220 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_5.5.24-0ubuntu0.12.04.1_all.deb) ...
Setting up mysql-server (5.5.24-0ubuntu0.12.04.1) ...
me@3MJ:~$ 
```Ok... so where do I put in the password?
It didn't ask me to set a password..?

---

### Post by steeldriver on 2012-09-23
Try running the dpkg-reconfigure again now

```
sudo dpkg-reconfigure mysql-server5.5
```

I just did an install-purge-reinstall to test things and it seems that only the initial  install prompts to set a root password - the reinstall doesn't (somehow  'purge' apparently isn't purging that part of the config)

---

### Post by felinoel on 2012-09-23
> **steeldriver said:**
> Try running the dpkg-reconfigure again now

```
sudo dpkg-reconfigure mysql-server5.5
``````
me@3MJ:~$ sudo dpkg-reconfigure mysql-server-5.5
[sudo] password for me: 
mysql stop/waiting
120923 11:57:36 [Note] Plugin 'FEDERATED' is disabled.
120923 11:57:36 InnoDB: The InnoDB memory heap is disabled
120923 11:57:36 InnoDB: Mutexes and rw_locks use GCC atomic builtins
120923 11:57:36 InnoDB: Compressed tables use zlib 1.2.3.4
120923 11:57:36 InnoDB: Initializing buffer pool, size = 128.0M
120923 11:57:36 InnoDB: Completed initialization of buffer pool
120923 11:57:36 InnoDB: highest supported file format is Barracuda.
120923 11:57:36  InnoDB: Waiting for the background threads to start
120923 11:57:37 InnoDB: 1.1.8 started; log sequence number 3307488
120923 11:57:37  InnoDB: Starting shutdown...
120923 11:57:38  InnoDB: Shutdown completed; log sequence number 3307488
mysql start/running, process 6127
me@3MJ:~$ 
me@3MJ:~$ 
me@3MJ:~$ sudo mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
me@3MJ:~$ 
```

> I just did an install-purge-reinstall to test things and it seems that only the initial  install prompts to set a root password - the reinstall doesn't (somehow  'purge' apparently isn't purging that part of the config)Sounds like a good reason to reinstall Ubuntu.

---

### Post by Habitual on 2012-09-23
> **felinoel said:**
> [code]...Sounds like a good reason to reinstall Ubuntu.

https://help.ubuntu.com/community/MysqlPasswordReset

---

### Post by felinoel on 2012-09-23
> **Habitual said:**
> https://help.ubuntu.com/community/MysqlPasswordReset

Pretty sure I tried this a week ago... guess I will see what happens now that it was purged. I assume that will make a difference.

---

### Post by felinoel on 2012-09-23
```
me@3MJ:~$ sudo /etc/init.d/mysql stop
[sudo] password for me: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mysql
mysql stop/waiting
me@3MJ:~$ sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking &
[1] 8100
me@3MJ:~$ 120923 21:34:50 [Note] Plugin 'FEDERATED' is disabled.
120923 21:34:50 InnoDB: The InnoDB memory heap is disabled
120923 21:34:50 InnoDB: Mutexes and rw_locks use GCC atomic builtins
120923 21:34:50 InnoDB: Compressed tables use zlib 1.2.3.4
120923 21:34:50 InnoDB: Initializing buffer pool, size = 128.0M
120923 21:34:50 InnoDB: Completed initialization of buffer pool
120923 21:34:50 InnoDB: highest supported file format is Barracuda.
120923 21:34:50  InnoDB: Waiting for the background threads to start
120923 21:34:51 InnoDB: 1.1.8 started; log sequence number 3307488
120923 21:34:51 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.5.24-0ubuntu0.12.04.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 0  (Ubuntu)


```

```
me@3MJ:~$ mysql -u root
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.5.24-0ubuntu0.12.04.1 (Ubuntu)

Copyright (c) 2000, 2011, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> FLUSH PRIVELEGES;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'PRIVELEGES' at line 1
mysql> 

```What went wrong?

---

### Post by steeldriver on 2012-09-23
speeling?

```
For either method, once have received a message indicating a successful query (one or more rows affected), flush privileges:

FLUSH [COLOR="Red"]PRIVILEGES[/COLOR];

Then stop themysqld process and relaunch it with the classical way:
```

---

### Post by felinoel on 2012-09-24
```
me@3MJ:~$ mysql -u root
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.5.24-0ubuntu0.12.04.1 (Ubuntu)

Copyright (c) 2000, 2011, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> FLUSH PRIVELEGES;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'PRIVELEGES' at line 1
mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.01 sec)

mysql> SET PASSWORD FOR root@'localhost' = PASSWORD('bill');
ERROR 1133 (42000): Can't find any matching row in the user table
mysql> 
```What went wrong now?

---

### Post by Habitual on 2012-09-24
```
UPDATE user SET Password=PASSWORD('YOURNEWPASSWORD') WHERE User='root'; FLUSH PRIVILEGES; exit;
```

[http://dev.mysql.com/doc/](http://dev.mysql.com/doc/)

---

### Post by felinoel on 2012-09-24
> **Habitual said:**
> ```
UPDATE user SET Password=PASSWORD('YOURNEWPASSWORD') WHERE User='root'; FLUSH PRIVILEGES; exit;
```

[http://dev.mysql.com/doc/](http://dev.mysql.com/doc/)

So... do that *instead *of [this](https://help.ubuntu.com/community/MysqlPasswordReset) then?

---

### Post by Habitual on 2012-09-24
> **felinoel said:**
> So... do that *instead *of [this]("https://help.ubuntu.com/community/MysqlPasswordReset") then?

Your mysql-server is now working, yes? If so, you can ignore [https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)
You want to change the mysql-root password, yes?
If yes, enter mysql > and paste this in:
```
UPDATE user SET Password=PASSWORD('[COLOR=Red]YOURNEWPASSWORD'[/COLOR]) WHERE User='root'; FLUSH PRIVILEGES; exit;
``` to change the mysql-root password.

---

### Post by felinoel on 2012-09-24
```
me@3MJ:~$ sudo mysql -u root
[sudo] password for me: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.5.24-0ubuntu0.12.04.1 (Ubuntu)

Copyright (c) 2000, 2011, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> UPDATE user SET Password=PASSWORD('Bill') WHERE User='root';
ERROR 1046 (3D000): No database selected
mysql> 


```I never was able to make a database..?

---

### Post by steeldriver on 2012-09-24
AFAIK the user table should be in database called 'mysql' - iirc you can either select the initial database on the command line, or from the mysql prompt (where you are now)

```
mysql> USE mysql;
```You can then set the password using your 'UPDATE' command - or if you're curious

```
mysql> SHOW tables;
```

---

### Post by felinoel on 2012-09-24
> **steeldriver said:**
> AFAIK the user table should be in database called 'mysql' - iirc you can either select the initial database on the command line, or from the mysql prompt (where you are now)

```
mysql> USE mysql;
```You can then set the password using your 'UPDATE' command - or if you're curious

```
mysql> SHOW tables;
```

```
mysql> UPDATE user SET Password=PASSWORD('Bill') WHERE User='root';
Query OK, 0 rows affected (0.01 sec)
Rows matched: 0  Changed: 0  Warnings: 0

```?!?!!!!!

---

### Post by steeldriver on 2012-09-24
Hmm.. well this is beyond my paygrade, all I can do is tell you what I see on my setup:

```
mysql> SELECT Host, User, Password, Update_priv from user;
+-----------+------------------+-------------------------------------------+-------------+
| Host      | User             | Password                                  | Update_priv |
+-----------+------------------+-------------------------------------------+-------------+
| localhost | root             | *D1FD34A61BA1EC4BB676ABC5017DCC7D079565E6 | Y           |
| lap-t61p  | root             | *D1FD34A61BA1EC4BB676ABC5017DCC7D079565E6 | Y           |
| 127.0.0.1 | root             | *D1FD34A61BA1EC4BB676ABC5017DCC7D079565E6 | Y           |
| ::1       | root             | *D1FD34A61BA1EC4BB676ABC5017DCC7D079565E6 | Y           |
| localhost |                  |                                           | N           |
| lap-t61p  |                  |                                           | N           |
| localhost | debian-sys-maint | *0C4AE561302CAE8B4F0613554E6C822B0A6536AF | Y           |
+-----------+------------------+-------------------------------------------+-------------+
7 rows in set (0.00 sec)

mysql> UPDATE user SET Password=PASSWORD('newpasswd') WHERE User='root';
Query OK, 4 rows affected (0.00 sec)
Rows matched: 4  Changed: 4  Warnings: 0

mysql> SELECT Host, User, Password, Update_priv from user;
+-----------+------------------+-------------------------------------------+-------------+
| Host      | User             | Password                                  | Update_priv |
+-----------+------------------+-------------------------------------------+-------------+
| localhost | root             | *4A32D081DC3E374F189AD2BD404398B7E88CADAA | Y           |
| lap-t61p  | root             | *4A32D081DC3E374F189AD2BD404398B7E88CADAA | Y           |
| 127.0.0.1 | root             | *4A32D081DC3E374F189AD2BD404398B7E88CADAA | Y           |
| ::1       | root             | *4A32D081DC3E374F189AD2BD404398B7E88CADAA | Y           |
| localhost |                  |                                           | N           |
| lap-t61p  |                  |                                           | N           |
| localhost | debian-sys-maint | *0C4AE561302CAE8B4F0613554E6C822B0A6536AF | Y           |
+-----------+------------------+-------------------------------------------+-------------+
7 rows in set (0.00 sec)

mysql> 

```If I try to UPDATE with the same password, it still matches but doesn't change

```
mysql> UPDATE user SET Password=PASSWORD('newpasswd') WHERE User='root';
Query OK, 0 rows affected (0.00 sec)
Rows matched: 4  Changed: 0  Warnings: 0

mysql> 

```

---

### Post by Wim Sturkenboom on 2012-09-25
in mysql

```

mysql> select user, password, host from user;
+----------+-------------------------------------------+-----------+
| user     | password                                  | host      |
+----------+-------------------------------------------+-----------+
[COLOR="Red"]| root     | *58364B2092FC2BF7A21616D9442D8250D2627B5B | localhost |[/COLOR]
| wim      | *C3745A8F16281DEB77AF3AB390ED713D6B666B0B | localhost |
| btd_user | *0E83ED58D08990E92CE26C13C7001A598FEA0C87 | localhost |
| tacinc   | *82A17FA00CB20A1A486DC912C5384755C4E84E0C | localhost |
| poepie   |                                           | localhost |
+----------+-------------------------------------------+-----------+
5 rows in set (0.01 sec)

mysql>

```
This is just to make sure that there is no root user. If there is a root user, skip the next part.

Next run the below statement to create a root user
```

mysql > GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' IDENTIFIED BY 'whateverpassword' WITH GRANT OPTION

```

Flush the privileges, exit mysql and restart the mysql daemon. Next try to connect with
```

wim@webserver:~$ mysql -u root -p

```

---

### Post by felinoel on 2012-09-25
Wait whats all this now? Wasn't I able to log in now?

---

### Post by Wim Sturkenboom on 2012-09-25
> **felinoel said:**
> Wait whats all this now? Wasn't I able to log in now?
No, you bypassed all access control which is a temporary measurement to fix things.

---

### Post by felinoel on 2012-09-26
> **Wim Sturkenboom said:**
> No, you bypassed all access control which is a temporary measurement to fix things.But... then I changed the password and reset it and logged in with the new password and the logging in worked?

Isn't mysql -u root -p just logging in as the root with a password and the standard and regular way to log in?

---

### Post by Wim Sturkenboom on 2012-09-27
> **felinoel said:**
> But... then I changed the password and reset it and logged in with the new password and the logging in worked?

Isn't mysql -u root -p just logging in as the root with a password and the standard and regular way to log in?

Sorry, it's not quite clear if (or that) your problem is solved. You've typed a pile of ????? in post #42.

If you don't use skip-grant-tables when starting the mysql daemon, than it's the 'normal' way.

But normal is relative ;)

As always, usage of an all powerful root user should be limited and handled with care. I only use the mysql root user to create databases and do mysql maintenance. Next I have a mysql user (wim) that has full permissions on every database; this user designs databases (create tables etc); but this user can not grant privileges to other users. And the last mysql user is btd_user who can only populate tables with data.

---

### Post by felinoel on 2012-09-27
> **Wim Sturkenboom said:**
> Sorry, it's not quite clear if (or that) your problem is solved. You've typed a pile of ????? in post #42.

If you don't use skip-grant-tables when starting the mysql daemon, than it's the 'normal' way.

But normal is relative ;)

As always, usage of an all powerful root user should be limited and handled with care. I only use the mysql root user to create databases and do mysql maintenance. Next I have a mysql user (wim) that has full permissions on every database; this user designs databases (create tables etc); but this user can not grant privileges to other users. And the last mysql user is btd_user who can only populate tables with data.I typed the ?s and !s because it said it worked?

I really only need a database made for this server at this time.

Relativity is relative, but uncertainty is certain... :-k

---

### Post by steeldriver on 2012-09-27
It said the query was OK - but it didn't change anything I think

> ```
mysql> UPDATE user SET Password=PASSWORD('Bill') WHERE User='root';
Query OK, 0 rows affected (0.01 sec)
Rows matched: 0  Changed: 0  Warnings: 0
```Wim Sturkenboom is the expert here but the way I read it the problem is (and probably has been from the start) that** your mysql.user table was missing the root user record **- removing / purging the mysql-server installation doesn't delete the table (in /var/lib/mysql by default) so no matter whether you reinstalled OR dpkg-reconfigured it didn't ever ask you to set a root password - hence the need to CREATE a root user as per Wim's most recent post

---

### Post by Wim Sturkenboom on 2012-09-27
steeldriver is right; the query did not change anything as it states "0 rows affected". I thought that you understood that and hence the question marks and exclamation marks

Just to make sure, run the select query from post #43 or #44 again; it must give you one or more root user(s).

If not, run the grant statement in post #44.

And a note:
Because you want one database for this server, don't ignore security practices.

And another one:
I'm not the specialist :)

---

### Post by felinoel on 2012-09-28
> **Wim Sturkenboom said:**
> steeldriver is right; the query did not change anything as it states "0 rows affected". I thought that you understood that and hence the question marks and exclamation marks

Just to make sure, run the select query from post #43 or #44 again; it must give you one or more root user(s).

If not, run the grant statement in post #44.

And a note:
Because you want one database for this server, don't ignore security practices.

And another one:
I'm not the specialist :)

> **steeldriver said:**
> It said the query was OK - but it didn't change anything I think

Wim Sturkenboom is the expert here but the way I read it the problem is (and probably has been from the start) that** your mysql.user table was missing the root user record **- removing / purging the mysql-server installation doesn't delete the table (in /var/lib/mysql by default) so no matter whether you reinstalled OR dpkg-reconfigured it didn't ever ask you to set a root password - hence the need to CREATE a root user as per Wim's most recent postI figured nothing changed but when I mysql -u root -p and typed in the password it let me sign in?

---

### Post by Wim Sturkenboom on 2012-09-28
Are you still running with --skip-grant-tables?

---

### Post by felinoel on 2012-10-02
> **Wim Sturkenboom said:**
> Are you still running with --skip-grant-tables?

I don't think so... how long does that stay in effect?

---

### Post by Habitual on 2012-10-02
> **felinoel said:**
> I don't think so... how long does that stay in effect?

until you restart the mysql-server service, or reboot.

---

### Post by felinoel on 2012-10-04
> **Habitual said:**
> until you restart the mysql-server service, or reboot.

Then no I guess I am not.

---

### Post by Habitual on 2012-10-04
If you have restarted mysql or the server, then the --skip-grant-tables will not be in effect and if you can login to mysql as root after that event with -uroot -p<pass> then you are good to go.

---

