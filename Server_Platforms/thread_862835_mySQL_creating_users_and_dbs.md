---
title: "mySQL creating users and dbs"
date: 2008-07-17
forum: Server Platforms
---

### Post by kubapl on 2008-07-17
So I'm trying to install Joomla 1.5 with little luck for some reason the mysql is giving be problems. I attempted to make a user and a db for joomla by doing this

```

 mysql -A -u root -p  
  Enter password: 
  Welcome to the MySQL monitor.  Commands end with ; or \g.
  Your MySQL connection id is 4 to server version: 5.0.20a-Debian_2-log
  
  Type 'help;' or '\h' for help. Type '\c' to clear the buffer.
  
  mysql> use mysql;
  Database changed
  mysql> insert into user (host, user, password) values ('localhost', 'joomla', password('thejoomlapassword'));  
  Query OK, 1 row affected, 3 warnings (0.00 sec)  
  
  mysql> insert into db (host, db, user, select_priv) values ('localhost', 'db_joomla', 'joomla', 'Y');
  Query OK, 1 row affected (0.00 sec)
  
  mysql> create database db_joomla;
  Query OK, 1 row affected (0.01 sec)

```

everything looks like it went threw but then when I go threw the joomla instalation on the threw the browser it gives me error

```

Unable to connect to the database:Could not connect to MySQL

```

...Any ideas what the problem may be?

---

### Post by cariboo on 2008-07-18
From the error message:

```
mysql> insert into user (host, user, password) values ('localhost', 'joomla', password('thejoomlapassword'));  
  Query OK, 1 row affected, **3 warnings** (0.00 sec)
```

It looks like your user joomla and it's password weren't created.

Can you log into mysql using the user you created?

```
mysql -u joomla -p db_joomla
```

Jim

---

### Post by kubapl on 2008-07-18
> **cariboo907 said:**
> 
Can you log into mysql using the user you created?


negative I get 
```

Error 1045 (28000): Access denied for user 'joomla'@'localhost' (using password: YES)

```

---

### Post by kubapl on 2008-07-18
anyone know what this error means ?

---

### Post by cariboo on 2008-07-19
The error means that joomla is not a valid user create a user like this:

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

substitute your user name for <user> and your password for <somepass>.

I might be an idea to install the mysql-doc-5.0 package.

Jim

---

### Post by kubapl on 2008-07-19
Cool thanks its all working now

---

