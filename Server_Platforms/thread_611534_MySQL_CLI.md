---
title: "MySQL CLI"
date: 2007-11-13
forum: Server Platforms
---

### Post by prodezigner on 2007-11-13
I'm wanting to go 100% CLI based on my server without installing additional extras for maintaining (SWAT, Webmin, myPHPadmin, etc.) as it's not really needed. I don't know anything about MySQL at all and was wondering if anyone had any simple tutorials on basic commands (such as creating and deleting databases) cause I just need a blank DB and nothing in it as the installer I need only needs the blank DB and I have NO CLUE what I'm doing.

---

### Post by twistedtwig on 2007-11-13
[http://anaturb.net/MySQL/mysql_commands.htm](http://anaturb.net/MySQL/mysql_commands.htm)

google is your friend with this one.  I recently wanted to figure out how to backup msyql via command line and mysqldump turned out to be great and many easy examples online.

GL

---

### Post by k_grdn on 2007-11-13
Hi,

Set the root password;

mysqladmin -u root  password 'mysqlrootpass'

To access mysql from shell;

mysql -u user -p 

mysql> use database database;

mysql> CREATE DATABASE dbname;

mysql>SHOW DATABASES;

mysql>SHOW TABLES;

Try: [http://dev.mysql.com/doc/](http://dev.mysql.com/doc/) for reference docs, also google for cheat sheets, will give you a good start.

Regards,

k_grdn

---

