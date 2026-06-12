---
title: "Mysql config issue in fresh 7.10 server install"
date: 2007-10-27
forum: Server Platforms
---

### Post by Chayak on 2007-10-27
This isn't the first time I've set up mysql on a webserver and to be honest this is a little frustrating as it's holding up deployment.  I've seen various 'fixes' on forums and most deal with editing the allow tables which simply errors when I try with *mysql*

```

mysqladmin -u root password *examplepassword*

27ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

sudo mysqladmin -u root -h localhost password *examplepassword*

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

```

This is a fresh 7.10 install so I'm left scratching my head.

So I did a version check, guess what? Same error

```
mysqladmin -u root version
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

```

I've checked the config files and it's on the local port and loopback address for localhost.  I've checked and the service is running and listening but I can't connect.  I've tried the mysql command and gotten the same 'ERROR 1045'.  I've already put a good deal of time in setting up this server so I'd like to find a fix.

---

### Post by whit on 2007-10-27
If you're quoting what you typed, that looks wrong. The syntax for mysql itself is:

mysql -u root -p<password> 

Note there's no space after the "-p" (couldn't tell you why). If IRC, mysqladmin is the same syntax.

---

### Post by Chayak on 2007-10-27
I've tried that as well.  It doesn't work.  Same error with root@localhost denied access

---

### Post by gnaunited on 2007-10-28
mysql -u root -p

Hit Enter

It will ask for a password

Did you set the root password?

---

### Post by Chayak on 2007-10-28
> **gnaunited said:**
> mysql -u root -p

Hit Enter

It will ask for a password

Did you set the root password?

It asks for the password but it's never let me set it so nothing I enter works.  I know it's suppose to be installed without a password for root and every previous time I've set it up has been that way and I've never had an issue.

---

### Post by Peter Riche on 2007-10-29
have you tried :
```
sudo -i mysql_secure_installation
```
it will ask for the root password (should be nothing) and offer you the opportunity to change it

have you tried uninstalling mysql-server and installing it again?

i've had problems with mysql-server and 7.10 (desktop but I think packages are the same...) because during the installation I saw debconf asking me for the mysql password, whereas in 7.04 (and older) it never did and just set an empty one

---

### Post by Chayak on 2007-10-29
It did something but I still get the same error 1045 when I hit enter or try to enter a password with that.  ](*,)

---

### Post by gkestrel on 2007-11-03
Try this in the terminal enter sudo dpkg-reconfigure mysql-server-5.0 this should allow you to set up a root password

---

### Post by ruibernardo on 2007-11-03
Since Gutsy the mysql root password is set on install. Even if you didn't set it in Feisty, when you upgrade to Gutsy the installer will say it's not set and will ask you to set it, so I find a bit strange when you say that you didn't set it and you want to set it now. 

gkestrel post should resolve your problem.

---

### Post by Railsbuntu on 2007-11-04
Hi,

if you are still having troubles, fully uninstall mysql by purging, then reinstall mysql, and as soon as it is finished with installation, the absolute first command you should use is:
```
sudo mysqladmin -u root password YourNewPassWord
```

I had the same problem as you, and that worked for me :guitar:

---

### Post by Chayak on 2007-11-07
Ok, the sudo dpkg-reconfigure fixed everything and I finally managed to get the server deployed.  Thanks for the assist.

---

### Post by rolex42 on 2007-11-08
Hi,

I have this problem om my freshly installed Ubuntu-7.10-server.
I have tried all the above commands but they all say "Access denied for user 'root'@'localhost' ".

Here is an example

# mysql_secure_installation

NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MySQL
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

In order to log into MySQL to secure it, we'll need the current
password for the root user.  If you've just installed MySQL, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none): 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
Enter current password for root (enter for none): 


Exactly how should the "dpkg-reconfigure " look like?

/Roland

---

### Post by Chayak on 2007-11-08
> **rolex42 said:**
> Hi,

I have this problem om my freshly installed Ubuntu-7.10-server.
I have tried all the above commands but they all say "Access denied for user 'root'@'localhost' ".

Here is an example

# mysql_secure_installation

NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MySQL
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

In order to log into MySQL to secure it, we'll need the current
password for the root user.  If you've just installed MySQL, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none): 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
Enter current password for root (enter for none): 


Exactly how should the "dpkg-reconfigure " look like?

/Roland

```
sudo dpkg-reconfigure mysql-server-5.0
```

---

### Post by rolex42 on 2007-11-09
Hi,

Logged in as root I did the following:

#  /etc/init.d/mysql stop
 * Stopping MySQL database server mysqld
   ...done.

# /usr/bin/mysqld_safe --skip-grant-tables --skip-networking &
[1] 7639
# Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[7679]: started

# mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.0.45-Debian_1ubuntu3-log Debian etch distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> use mysql
Database changed

mysql> select user,host from user;
+------------------+-----------+
| user             | host      |
+------------------+-----------+
| root             | 127.0.0.1 | 
| debian-sys-maint | localhost | 
| root             | localhost | 
| root             | rolex     | 
+------------------+-----------+
4 rows in set (0.00 sec)

mysql> UPDATE mysql.user SET Password=PASSWORD('mysecret') where User='root'; 
Query OK, 3 rows affected (0.00 sec)
Rows matched: 3  Changed: 3  Warnings: 0

mysql> flush privileges; 

#  /etc/init.d/mysql stop

#  /etc/init.d/mysql start

**And Voilá!**
# mysql -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 5.0.45-Debian_1ubuntu3-log Debian etch distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 


Thanks for your posting here folks. It helped me.[http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)
:popcorn:

---

