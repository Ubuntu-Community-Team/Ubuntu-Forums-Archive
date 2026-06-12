---
title: "Setting up forum"
date: 2006-07-05
forum: Server Platforms
---

### Post by jordans on 2006-07-05
Hi, I am setting up a forum on my website and was wondering if some one could help me. 
Enter then name of your database 					 						The name of the database that PunBB will be installed into. The database must exist. For SQLite, this is the relative path to the database file. If the SQLite database file does not exist, PunBB will attempt to create it.
 						**(then a box to enter the name)**

How do I create a database or do I already have one?
Thanks,
Jordan

---

### Post by Randomskk on 2006-07-05
Have you installed MySQL?
something like sudo apt-get install mysql-server-5.0 should work, once you've done that you need to add the database.
The easiest way is probably with phpmyadmin:
sudo apt-get install phpmyadmin
[http://SERVERIP/phpmyadmin](http://SERVERIP/phpmyadmin)

Have a look here for some more information:
[https://help.ubuntu.com/community/ApacheMySQLPHP#head-27bbd09e3c1b26b978a72c40862fa17a4f9e1af4](https://help.ubuntu.com/community/ApacheMySQLPHP#head-27bbd09e3c1b26b978a72c40862fa17a4f9e1af4)

---

### Post by jordans on 2006-07-05
well. it can't find ipaddress/phpmyadmin
any ideas?

---

### Post by Randomskk on 2006-07-05
Have you installed it?
sudo apt-get install phpmyadmin

Also, is your web document root elsewhere than /var/www?
If you go to /var/www you'll see the phpmyadmin folder, move it to wherever is needed. (It's a symlink)

---

### Post by jordans on 2006-07-05
Well, I got into phpmyadmin but got this error when i tried to login
#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)

---

### Post by Randomskk on 2006-07-05
And did you install MySQL?
sudo apt-get install mysql-server-5.0

---

### Post by jordans on 2006-07-05
Didn't like the package name
But I am pretty sure it was installed. Is there another name I should try?

---

### Post by jordans on 2006-07-05
and also, i just figured out that you do apt-get install mysql-server and that works. But the socket file doesn't excist, what do i do, can i copy the file to there from some place on the web?

---

### Post by Randomskk on 2006-07-05
Oops, server-5.0 is for Dapper only, sorry.
Once you do apt-get install mysql-server, MySQL should start and the socket file should be made - have you looked at the link to the Ubuntu Wiki I gave?
That page specifies a few things you can do after installation of MySQL.

If it's installed but doesn't seem to be running, try:
sudo /etc/init.d/mysql restart

---

### Post by jordans on 2006-07-05
I tried restarting and all it said was to make sure the file excists which it doesn't. I tried reinstalling the thing but still no such luck. The link you gave me won't help till it starts to run and can actually start.

---

### Post by jordans on 2006-07-05
Can you help me using Gtalk? my account is [email]jordansoltman@gmail.com[/email] if this is at all a possibility. Thanks!

---

### Post by jordans on 2006-07-05
Can some one please help me figure out what is going on with setting up MySQL. When I try to start it it says: Check that mysqld is running and that the sockedt: '/var/run/mysqld/mysqld.sock' exists!
Well I checked and it doesn't exist. I don't know what is wrong but I need it to work. I have reinstalled and rebooted, the works.
Please help!
Jordan

---

### Post by Randomskk on 2006-07-06
Hey
Sorry, it was getting pretty late in the UK so I went to sleep, but I'm up now - once you're online, grab me on gTalk (my address is in my profile) and I can help you out there.

---

### Post by az on 2006-07-06
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

mysql -u root

mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourmysqlrootpassword');

mysql>CREATE DATABASE punbb;

mysql> GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES ON punbb.* TO 'yourusername'@'localhost' IDENTIFIED BY 'yourpassword';

mysql> FLUSH PRIVILEGES;

mysql> \q

Where:
yourmysqlrootpassword = the password you give to the mysql-root user.  (The database has users and one of them is root.  You first give it a password)

the name of your database is punbb

yourusername = the mysql user with less privileges which the punbb software will use to access the database.

yourpassword = yourusername's password

---

### Post by az on 2006-07-06
I forgot.  If you have already set a mysql root password, you need to start mysql with the -p flag:

mysql -u root -p

and enter the root password.  Then go ahead and CREATE DATABASE....

---

### Post by jordans on 2006-07-07
Yes, when i typed the first command you told me too it just told me it couldn't find the socket.

---

### Post by az on 2006-07-08
I wrote a page detailing how to install PunBB.  I hope that helps.

Make sure that you have the correct version of Apache2, php5 and mysql-server installed.

[https://help.ubuntu.com/community/PunBB](https://help.ubuntu.com/community/PunBB)

---

