---
title: "Can't Add new MySql Users"
date: 2008-06-23
forum: Server Platforms
---

### Post by randomorbit on 2008-06-23
Hi.  I searched the forum and didn't see anything like this, so please forgive me if this was answered elsewhere.  I have Ubuntu 8.04 server edition installed.  I installed MySQL (version 5.0.51a-3ubuntu5.1), and it's running OK, except when I try to add users to MySQL, it gives me an access denied message.  I can access MySQL as root just fine:

user@ubuntu:~$ mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 10
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> grant all on *.* to test identified by 'testing123';
Query OK, 0 rows affected (0.00 sec)

mysql> SHOW GRANTS FOR test;
+--------------------------------------------------------------------------------------------------------------+
| Grants for test@%                                                                                            |
+--------------------------------------------------------------------------------------------------------------+
| GRANT ALL PRIVILEGES ON *.* TO 'test'@'%' IDENTIFIED BY PASSWORD 'xxxxxxxxxxx' |
+--------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.00 sec)

mysql> exit
Bye
user@ubuntu:~$ mysql -u test -p
Enter password:
ERROR 1045 (28000): Access denied for user 'test'@'localhost' (using password: YES)
userk@ubuntu:~$

Can someone please help?

Thanks!

---

### Post by rogier.de.groot on 2008-06-23
Two things I can think of:
a) By default the mysql commandline client connects to a database with the same name as the user (in this case "test"); maybe the "test" database doesn't exists: try "mysql -u test -p mysql" instead.
b) Maybe you should change the IP MySQL listens on for network connections: edit /etc/mysql/my.cnf (or similar, I vaguely recall having a 5 somewhere in the path) to make it listen on other interfaces.
Good luck!

---

### Post by Martyn Thompson on 2008-06-23
Have you checked that the user and host appear correctly in the mysql database? 

Once logged in to the mysql server > use mysql; to change to that database. 

Then select Host, User, Password from user;   (note capitalisations). 

This will at least show you if the new user has been added to the database itself. 

Let us know how you get on...

Martyn.

---

### Post by randomorbit on 2008-06-23
Thanks for the suggestion!  Your tip gave me some insight.

What I found was several "localhost" entries, one with blank fields in it.  I deleted it and all seems to be working.

Thanks to all!

---

### Post by cariboo on 2008-06-24
The way I usually set up a new user is like this:

```
mysql> GRANT ALL PRIVILEGES ON *.* TO user@localhot
    -> IDENTIFIED BY '**********' WITH GRANT OPTION;
Query OK, 0 rows affected (0.00 sec)

mysql> GRANT ALL PRIVILEGES ON *.* TO user@'%'
    -> IDENTIFIED BY '**********' WITH GRANT OPTION;
Query OK, 0 rows affected (0.00 sec
```

Then Flush Privileges

Jim

---

