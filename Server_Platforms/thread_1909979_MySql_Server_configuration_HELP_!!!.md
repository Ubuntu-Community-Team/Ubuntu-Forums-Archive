---
title: "MySql Server configuration HELP !!!"
date: 2012-01-16
forum: Server Platforms
---

### Post by vikkyhacks on 2012-01-16
I downloaded lampp and installed int inside /opt/~~~ directory. I went to the /opt/lampp/bin directory and executed mysql to try out some commands which i did in my college but get an error message as shown in the end --> "CANNOT CONNECT TO DATABASE" ... I understand that i need to create user and also need to make some adjustments .. I tried to use some e-books but all in vain... Please HELP ME TO CONFIGURE MY SQL SERVER SO THAT I CAN TRY OUT MY DML AND DDL commands....I am really new to this ... Any good links to some tutorials would help me, I am completely at sea :confused::confused::confused:....


[FONT="Arial"][I]/opt/lampp/lampp start
Starting XAMPP for Linux 1.7.4...
XAMPP: Starting Apache...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
root@VikkyHacks:~# nmap -sS -p 0-10000 192.168.35.1

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2012-01-16 20:17 IST
Nmap scan report for 192.168.35.1
Host is up (0.000010s latency).
Not shown: 9996 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
80/tcp   open  http
443/tcp  open  https
902/tcp  open  iss-realsecure
3306/tcp open  mysql
root@VikkyHacks:/opt/lampp/bin# ./mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.5.8 Source distribution

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> create table example (name varchar(5));
ERROR 1046 (3D000): No database selected
mysql> 
[/I][/FONT]

---

### Post by Dangertux on 2012-01-16
> **vikkyhacks said:**
> I downloaded lampp and installed int inside /opt/~~~ directory. I went to the /opt/lampp/bin directory and executed mysql to try out some commands which i did in my college but get an error message as shown in the end --> "CANNOT CONNECT TO DATABASE" ... I understand that i need to create user and also need to make some adjustments .. I tried to use some e-books but all in vain... Please HELP ME TO CONFIGURE MY SQL SERVER SO THAT I CAN TRY OUT MY DML AND DDL commands....I am really new to this ... Any good links to some tutorials would help me, I am completely at sea :confused::confused::confused:....


[FONT=Arial][I]/opt/lampp/lampp start
Starting XAMPP for Linux 1.7.4...
XAMPP: Starting Apache...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
root@VikkyHacks:~# nmap -sS -p 0-10000 192.168.35.1

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2012-01-16 20:17 IST
Nmap scan report for 192.168.35.1
Host is up (0.000010s latency).
Not shown: 9996 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
80/tcp   open  http
443/tcp  open  https
902/tcp  open  iss-realsecure
3306/tcp open  mysql
root@VikkyHacks:/opt/lampp/bin# ./mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.5.8 Source distribution

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> create table example (name varchar(5));
ERROR 1046 (3D000): No database selected
mysql> 
[/I][/FONT]

You need to either create the database or you can use the mysql database

```

CREATE DATABASE database;
GRANT ALL PRIVILEGES ON database.* TO username@localhost IDENTIFIED BY 'password';
FLUSH PRIVILEGES;
USE database;
CREATE TABLE example(name varchar(5));

```

Hope this helps.

---

### Post by vikkyhacks on 2012-01-16
Thank You very much for the quick reply ..... but I get this error message on typing the very first command

[FONT="Arial"][I]mysql> CREATE DATABASE database;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'database' at line 1[/I][/FONT]:confused::confused:

---

### Post by Cheesemill on 2012-01-16
Are you allowed to call it database?

database might be a reserved name so I'd try with something else.

---

### Post by cabaro on 2012-01-16
I think 'database' is preserved word in mysql syntax so you cannot name your database database.

Try something like 

CREATE DATABASE 'mydatabase';

---

### Post by Dangertux on 2012-01-16
> **cabaro said:**
> I think 'database' is preserved word in mysql syntax so you cannot name your database database.

Try something like 

CREATE DATABASE 'mydatabase';


Yeah it's reserved. For clarification

database = your database name
username = the username you want to have access to the database
password = the password of the user.

Guess I should have said I was using it as a placeholder, didn't think you'd actually call it database. My fault.

---

### Post by vikkyhacks on 2012-01-16
**Thanks for the help 'IT WORKED !!' ..... **That solves all my basic questions till now and can create and use a database for now .... But are there any tutorials on any other website which would help me configure my sql server ... The books that i use only teach me creating, editing and modifying existing databases .... I need to know about the other commands like these cos even now I don understand anything in those above commands other than first line CREATE DATABASE <db_name> .... As you can see I am a real noob to these king of stuff ....

---

