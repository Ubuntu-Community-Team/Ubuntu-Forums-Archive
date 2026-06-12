---
title: "Server 8.04.1 mysql command line login problems"
date: 2008-07-11
forum: Server Platforms
---

### Post by saint_jude on 2008-07-11
I cannot login to mysql via the commandline in Ubuntu Server 8.04.1.  I re-installed the system to make sure there were no configuration errors. (I installed Ubuntu Server 8.04 i386 from disc, then ran 'apt-get upgrade')

I have a php app (osticket) installed that uses the database successfully as 'root' user.  However, when attempting to login to the mysql commandline using 'mysql -u root' I experience the error in this wiki post - [https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

After performing the steps in that wiki post, the error is still not resolved.  I have reset the password and then restarted MySQL and i cannot login as admin.  The php app (osticket) still works and connects to mysql successfully.

I have also performed these steps with AppArmor disabled.

```
nonroot@osthelpdesk:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
nonroot@osthelpdesk:~$ sudo /etc/init.d/mysql stop
[sudo] password for nonroot:
 * Stopping MySQL database server mysqld                                 [ OK ]
nonroot@osthelpdesk:~$ sudo /usr/sbin/mysqld --skip-grant-tables
080711 14:37:38  InnoDB: Started; log sequence number 0 43655
080711 14:37:38 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.0.51a-3ubuntu5.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)


nonroot@osthelpdesk:~$ mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 2
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.
mysql> UPDATE mysql.user SET Password=PASSWORD('password') WHERE User='root';
Query OK, 3 rows affected (0.02 sec)
Rows matched: 3  Changed: 3  Warnings: 0

mysql> exit
Bye
nonroot@osthelpdesk:~$ sudo /etc/init.d/mysql stop
[sudo] password for nonroot:
 * Stopping MySQL database server mysqld                                 [ OK ]
nonroot@osthelpdesk:~$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                 [ OK ]
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
nonroot@osthelpdesk:~$ sudo mysql -u root -password password
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
nonroot@osthelpdesk:~$ sudo mysql -u root -password 'password'
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
nonroot@osthelpdesk:~$
```

---

### Post by unixbills on 2008-07-11
I am not an sql person but may be able to help.

"root" and "root@localhost" are not the same.  You set the password for "root" but the system sees you as "root@localhost".  You want to set the password for 'root'@'localhost'.  You missed a step.  You need to do it again so you can get in as root and then follow all of the steps.  You want this part:

```

SET PASSWORD FOR root@'localhost' = PASSWORD('password');

```

I think maybe you can get in now with no password.

---

### Post by saint_jude on 2008-07-14
I tried your code with and without the "--skip-grant-tables" option.  Both times the command failed.  


MySQL started normally:
```
mysql>SET PASSWORD FOR root@'localhost' = PASSWORD('password');
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'mysql'

```

MySQL started with --skip-grant-tables
```

mysql> SET PASSWORD FOR root@'localhost' = PASSWORD('password');
ERROR 1290 (HY000): The MySQL server is running with the --skip-grant-tables option so it cannot execute this statement
```


Then I tried updating the mysql.user table with a modified update query (where host was specified).  See below:


mysql is running with --skip-grant-tables...
```

mysql> UPDATE mysql.user SET Password=PASSWORD('password') WHERE User='root' AND Host='localhost';
Query OK, 0 rows affected (0.00 sec)
Rows matched: 1  Changed: 0  Warnings: 0

mysql> SELECT User, Password, Host FROM mysql.user;
+------------------+-------------------------------------------+-------------+
| User             | Password                                  | Host        |
+------------------+-------------------------------------------+-------------+
| root             | *2470C0C06DEE42FD1618BB99005ADCA2EC9D1E19 | localhost   |
| root             | *2470C0C06DEE42FD1618BB99005ADCA2EC9D1E19 | osthelpdesk |
| root             | *2470C0C06DEE42FD1618BB99005ADCA2EC9D1E19 | 127.0.0.1   |
|                  |                                           | localhost   |
|                  |                                           | osthelpdesk |
| debian-sys-maint | *4FE45312C28AEF93B59F27609E333076D06C3454 | localhost   |
+------------------+-------------------------------------------+-------------+
6 rows in set (0.01 sec)

mysql> exit
Bye
nonroot@osthelpdesk:~$ sudo /etc/init.d/mysql stop
 * Stopping MySQL database server mysqld                                 [ OK ]
nonroot@osthelpdesk:~$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                 [ OK ]
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
nonroot@osthelpdesk:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
nonroot@osthelpdesk:~$ mysql -u root -password password
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
nonroot@osthelpdesk:~$ sudo mysql -u root -password password
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```

Still not working...

---

### Post by Pacendrix on 2008-08-20
Hello

I guess you are using MySQL version 5.0.51 , like me :)

So here comes its new syntax :)

The option's mark and its contents should be merged. 

So, here is the true command line:

```


mysql -uroot -ppassword


```

Where "root" is your username and "password" is the password that belongs to it.


P.S.
Man, I really don't understand why have they done it in this merged syntax :))

---

### Post by Ximbiot on 2008-08-20
> **Pacendrix said:**
> ```
mysql -uroot -ppassword
```

Yes, that should work.  To be prompted for the password rather than putting it on the command line, you can do this too:

```
mysql -uroot -p
```

When you put the password on the command line, it can be viewed via the `ps' and `top' commands until the command exits and in your shell's command history indefinitely.

---

### Post by Pacendrix on 2008-08-21
Ximbiot I just wanted to explain that it should be merged ...

However  you are right ... Security at first :)

Best Regards

---

