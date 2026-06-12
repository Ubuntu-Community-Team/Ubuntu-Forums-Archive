---
title: "Problem on Mysql - only root can login"
date: 2008-09-26
forum: Server Platforms
---

### Post by satimis on 2008-09-26
Hi folks,


Having tried > 2 hours without a solution.  Users can't login Mysql, passwords being correct.


Steps performed as follow;

$ mysql -u user -p```

Enter password: some_password
ERROR 1045 (28000): Access denied for user 'user'@'localhost' (using password: YES)

```

$ sudo /etc/init.d/mysql start```

Password:
Starting MySQL database server: mysqld already running.

```

$ mysql -uroot -p```

Enter password:
Welcome to the MySQL monitor.  Commands end ....

mysql> GRANT ALL PRIVILEGES ON *.* TO user@"%"
    -> IDENTIFIED BY 'some_password' WITH GRANT OPTION;
Query OK, 0 rows affected (0.11 sec)

mysql> exit
Bye

```

$ mysql -u user -p```

Enter password: some_password
ERROR 1045 (28000): Access denied for user 'user'@'localhost' (using password: YES)

```


$ sudo /etc/init.d/mysql start```

Starting MySQL database server: mysqld already running.

```

$ mysql -u user -p```

Enter password:
ERROR 1045 (28000): Access denied for user 'user'@'localhost' (using password: YES)

```

Please help.  TIA


B.R.
satimis

---

### Post by volkswagner on 2008-09-26
I would say the password is incorrect for "user", or user does not have permission to access the database from the address/host he is using (localhost).

When you added user, did you specify from localhost?

```
mysql -u root -p
(here I enter 'my_root_password' to get through the mysql prompt)

create database my_database;

GRANT ALL PRIVILEGES 
ON my_database.* 
TO 'user'@'localhost'
IDENTIFIED BY 'my_password' 
WITH GRANT OPTION;
```

---

### Post by satimis on 2008-09-26
Hi volkswagner,


Thanks for your advice.

> **volkswagner said:**
> I would say the password is incorrect for "user", or user does not have permission to access the database from the address/host he is using (localhost).

The password is correct.  Not only one user can't login.  I just recreate a new password for userA inside mysql.


> 
When you added user, did you specify from localhost?

Sorry I can't recall.  How to check it?  Or how to recreate it?  TIA


B.R.
satimis

---

### Post by volkswagner on 2008-09-26
The syntax is in my first post.  You may want to limit the grant privileges if you want the user to have limited control.  The privileges will be for only the databases you list.

EDIT:  I just noticed in your first post adding user, there was not changes to the database.  Was this the first time running the command?

---

### Post by kamaji792 on 2008-09-26
Hi all,

I am new to MySQL but I had a similar problem with my MySQL setup.  My solution was to create a user and specify the user and host.
```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'user'@'some_host'
    -> IDENTIFIED BY 'some_password' WITH GRANT OPTION;

```
**some_host** can be **localhost**

When I used phpMyAdmin to look at the users there was a '%'@'localhost' user.  I suspect this of causing problems when trying to authenticate a user 'user'@'%' when they attach from the local host.  I did remove the account but I can't remember if that was important as well as above.

All the best.

---

### Post by satimis on 2008-09-26
Hi kamaji792,


Thanks for your advice.


> **kamaji792 said:**
> Hi all,

I am new to MySQL but I had a similar problem with my MySQL setup.  My solution was to create a user and specify the user and host.
```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'user'@'some_host'
    -> IDENTIFIED BY 'some_password' WITH GRANT OPTION;

```
**some_host** can be **localhost**


Your advice works for me, using 'user'@'localhost'.  No further action needs.  Now user can login mysql.


B.R.
satimis

---

