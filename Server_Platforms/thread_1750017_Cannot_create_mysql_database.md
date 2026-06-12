---
title: "Cannot create mysql database"
date: 2011-05-05
forum: Server Platforms
---

### Post by Ango on 2011-05-05
I've struggled with this problem for a couple of days and I've run out of ideas. 

I've been trying to install Drupal on my laptop and everything seems to go well until I try to create a database under Mysql. I installed (and done a re-install) of Mysql server and client using sudo apt-get mysql to no avail.

I always get the error 

> CREATE DATABASE failed; error: 'Can't create database 'drupal' (errno: 13)'

I also tried to check the problem with phpmyadmin, but despite logging with as "root" I always end up with the following screen.

[IMG]http://www.expatypus.com/download/mysql_problem.png[/IMG]

Any help would be very much appreciated. I'm desperate.

---

### Post by elico on 2011-05-05
it's on the screen: no priviliges...
are you using root?
look at this:
[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

---

### Post by hawk2010 on 2011-05-05
I'm pretty sure that you have not logged in as root and as a normal user and this user has not been given any database privileges or to create one. 

QUOTE=Ango;10772005]I've struggled with this problem for a couple of days and I've run out of ideas. 

I've been trying to install Drupal on my laptop and everything seems to go well until I try to create a database under Mysql. I installed (and done a re-install) of Mysql server and client using sudo apt-get mysql to no avail.

I always get the error 



I also tried to check the problem with phpmyadmin, but despite logging with as "root" I always end up with the following screen.

[IMG]http://www.expatypus.com/download/mysql_problem.png[/IMG]

Any help would be very much appreciated. I'm desperate.[/QUOTE]

---

### Post by Ango on 2011-05-05
I tried both method (reset and purge) several times. To no avail.

The Mysql uninstall / install goes smoothly, I set a root password, which seems to work when I secure the database but stops working as soon as i try to log into the MySQL command-line client as the root user :confused:

> jacques@Booba:~$ sudo mysql_install_db
Installing MySQL system tables...
OK
Filling help tables...
OK

To start mysqld at boot time you have to copy
support-files/mysql.server to the right place for your system

PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
To do so, start the server, then issue the following commands:

/usr/bin/mysqladmin -u root password 'new-password'
/usr/bin/mysqladmin -u root -h pc password 'new-password'

Alternatively you can run:
/usr/bin/mysql_secure_installation

which will also give you the option of removing the test
databases and anonymous user created by default.  This is
strongly recommended for production servers.

See the manual for more instructions.

You can start the MySQL daemon with:
cd /usr ; /usr/bin/mysqld_safe &

You can test the MySQL daemon with mysql-test-run.pl
cd /usr/mysql-test ; perl mysql-test-run.pl

Please report any problems with the /usr/scripts/mysqlbug script!

jacques@Booba:~$ mysql_secure_installation




NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MySQL
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!


In order to log into MySQL to secure it, we'll need the current
password for the root user.  If you've just installed MySQL, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none): 
OK, successfully used password, moving on...

Setting the root password ensures that nobody can log into the MySQL
root user without the proper authorisation.

You already have a root password set, so you can safely answer 'n'.

Change the root password? [Y/n] n
 ... skipping.

By default, a MySQL installation has an anonymous user, allowing anyone
to log into MySQL without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] n
 ... skipping.

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] y
 ... Success!

By default, MySQL comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] y
 - Dropping test database...
ERROR 1008 (HY000) at line 1: Can't drop database 'test'; database doesn't exist
 ... Failed!  Not critical, keep moving...
 - Removing privileges on test database...
 ... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] y
 ... Success!

Cleaning up...



All done!  If you've completed all of the above steps, your MySQL
installation should now be secure.

Thanks for using MySQL!


jacques@Booba:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
jacques@Booba:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)


---

### Post by Ricalsin on 2011-05-05
The Natty release had some problems that affected mysql.  Check this thread out: [http://ubuntuforums.org/showthread.php?p=10774151#post10774151](http://ubuntuforums.org/showthread.php?p=10774151#post10774151)  It might help you out.

---

### Post by Ango on 2011-05-05
It  worked !
Thanks a million Ricalsin :D

---

### Post by Ricalsin on 2011-05-06
Cool.  Nice to see the smile.  Make sure to mark your thread as "solved"

---

