---
title: "Can't crate new databases in Mysql"
date: 2008-07-18
forum: Server Platforms
---

### Post by masoud23 on 2008-07-18
Hi

i run Xampp when i open phpmyadmin in localhost i see this rows:

Create new database: Documentation
No Privileges

---

### Post by cariboo on 2008-07-19
When you log into phpmyadmin do you log in as a user that has the privileges needed to create a database. If not you can create a user like this:

```
user@intrepid:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 2
Server version: 5.0.51a-6ubuntu3 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> grant all privileges on *.* to <user>@localhost
    -> identified by '<somepass>' with grant option;
Query OK, 0 rows affected (0.00 sec)

mysql> grant all privileges on *.* to <user>@'%'
    -> identified by '<somepass>' with grant option;
Query OK, 0 rows affected (0.00 sec)

mysql>flush privileges;
```

substitute your user name for <user> and your password for <somepass>

Jim

---

### Post by Francewhoa on 2009-06-21
To be able to create new database in phpMyAdmin you must login as ROOT.
I posted the solution at: [http://ubuntuforums.org/showpost.php?p=7495362&postcount=3](http://ubuntuforums.org/showpost.php?p=7495362&postcount=3)

---

