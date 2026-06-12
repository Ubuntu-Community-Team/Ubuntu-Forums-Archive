---
title: "mysql:  ''@'localhost' is able to login -- user doesn't exist!"
date: 2008-12-08
forum: Server Platforms
---

### Post by davidshere on 2008-12-08
When I login as root to my newly installed MySQL 5 on Ubuntu 8.04, I am able to show all the users:

```
david@blackwidow:~$ mysql -u root -p 
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 17
Server version: 5.0.51a-3ubuntu5.4 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> show grants;
+----------------------------------------------------------------------------------------------------------------------------------------+
| Grants for root@localhost                                                                                                              |
+----------------------------------------------------------------------------------------------------------------------------------------+
| GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' IDENTIFIED BY PASSWORD '*****************************************' WITH GRANT OPTION | 
+----------------------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> Bye
```

Clearly ''@'localhost' is not one of them.  However, I am able to login as that user:

```
david@blackwidow:~$ mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 19
Server version: 5.0.51a-3ubuntu5.4 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
+--------------------+
1 row in set (0.01 sec)

mysql> create database bob;
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'bob'
mysql> Bye
```

Any idea why this is possible?

---

### Post by cdenley on 2008-12-08
The show grants command show all grants for the specified user, or the current user if one is not specified. If you run it as 'root'@'localhost', and don't specify a user, then of course the grants for ''@'localhost' won't be listed. It doesn't mean they aren't there.
[http://dev.mysql.com/doc/refman/5.0/en/show-grants.html](http://dev.mysql.com/doc/refman/5.0/en/show-grants.html)
```
show grants for ''@'localhost';
```

---

### Post by davidshere on 2008-12-08
Okay... 
```
david@blackwidow:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 20
Server version: 5.0.51a-3ubuntu5.4 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> show grants for ''@'localhost';
+--------------------------------------+
| Grants for @localhost                |
+--------------------------------------+
| GRANT USAGE ON *.* TO ''@'localhost' | 
+--------------------------------------+
1 row in set (0.00 sec)

mysql> 


```

makes sense now I guess.

Thanks!

---

