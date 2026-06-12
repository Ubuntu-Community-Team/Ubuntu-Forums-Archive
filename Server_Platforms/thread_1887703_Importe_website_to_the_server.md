---
title: "Importe website to the server"
date: 2011-11-27
forum: Server Platforms
---

### Post by barezi6 on 2011-11-27
Hi everyone.
i have a website with all the code and database, and i am using the linux 8.04LTS version, the code is all to var/www and the database where it will stay?, when i was building  the website i use localhost (xampp) to the databse, my database is a mysql file, now i exported the database from xampp and now need to import it to the server, but need to know where and if i need to do some configuration etc.
Thanks

---

### Post by artjomtro on 2011-11-27
do you have installed mysql-server?

if no use this
```
[SIZE=2]sudo apt-get install mysql-server-5.0[/SIZE]
```enter your password for mysql root user [SIZE=1][SIZE=2]**yourpassword**[/SIZE][/SIZE]

if yes you need to create database and import it

use this :
1) create mysql database:
```
[SIZE=1][SIZE=2][B]mysql -u root -p 
CREATE DATABASE mydatabasename[/B][/SIZE][/SIZE]
```2)import database from your .sql file
```
[SIZE=2]mysql -hlocalhost  -uroot  -p[/SIZE][SIZE=2]**yourpassword** [/SIZE][SIZE=2]**mydatabasename** < [/SIZE][SIZE=2][B]database.sql

exit[/B][/SIZE]
```it's all )

---

### Post by barezi6 on 2011-12-04
> **artjomtro said:**
> do you have installed mysql-server?

if no use this
```
[SIZE=2]sudo apt-get install mysql-server-5.0[/SIZE]
```enter your password for mysql root user [SIZE=1][SIZE=2]**yourpassword**[/SIZE][/SIZE]

if yes you need to create database and import it

use this :
1) create mysql database:
```
[SIZE=1][SIZE=2][B]mysql -u root -p 
CREATE DATABASE mydatabasename[/B][/SIZE][/SIZE]
```2)import database from your .sql file
```
[SIZE=2]mysql -hlocalhost  -uroot  -p[/SIZE][SIZE=2]**yourpassword** [/SIZE][SIZE=2]**mydatabasename** < [/SIZE][SIZE=2][B]database.sql

exit[/B][/SIZE]
```it's all )

thanks for the help, but i am not understanding this part, my sql file is saved on my normal pc and i use filezilla to control the files on my server and i will to the server and create database etc, but after how i can import the file to the server?by a usb pen?can do it by filezilla?

and another doubt, normally when we use xampp or other localhost service on our computers, on the "mysqlconnection" inside the code of the website, we need to use some like it:

Mysql Connection    

$MYSQL['host'] = 'localhost';
$MYSQL['user'] = 'root';
$MYSQL['pass'] = '';
$MYSQL['data'] = 'database_name';
$con = @mysql_connect($MYSQL['host'], $MYSQL['user'], $MYSQL['passs']);

and now when it is used on a server, what change?

$MYSQL['host'] = 'localhost';----this part what change?
$MYSQL['user'] = 'root';----i know
$MYSQL['pass'] = 'mypass'; ----i know
$MYSQL['data'] = 'database_name'; ----i know

Thanks

---

### Post by barezi6 on 2011-12-05
up

---

