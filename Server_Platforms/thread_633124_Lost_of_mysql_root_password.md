---
title: "Lost of mysql root password"
date: 2007-12-06
forum: Server Platforms
---

### Post by satimis on 2007-12-06
Hi folks,


Ubuntu 7.04 server amd64
mysql-server 5.0.38
mysql-admin 1.2.5rc-1
mysql-admin-common 1.2.5rc-1
mysql-client 5.0.38
libmysqlclient15-dev 5.0.38

$ sudo mysql -u root mysql```

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```

Please advise how to recreate new mysql root password w/o the old password? TIA


B.R.
satimis

---

### Post by MJN on 2007-12-06
A Google search would've found this in less time than it took for you to make your post!
 
To speed things up, here's one way:
 
[http://www.cyberciti.biz/tips/recover-mysql-root-password.html](http://www.cyberciti.biz/tips/recover-mysql-root-password.html)
 
Mathew

---

### Post by satimis on 2007-12-06
> **MJN said:**
> A Google search would've found this in less time than it took for you to make your post!
 
To speed things up, here's one way:
 
[http://www.cyberciti.biz/tips/recover-mysql-root-password.html](http://www.cyberciti.biz/tips/recover-mysql-root-password.html)
 
Mathew
Thanks for your URL.  I tried it before including some other links.


Performed following steps;


# /etc/init.d/mysql stop```

 * Stopping MySQL database server mysqld                                 [ OK ] 

```

# mysqld_safe --skip-grant-tables &```

[1] 8106
root@mail:/home/satimis# Starting mysqld daemon with databases from /var/lib/mys
ql
mysqld_safe[8145]: started
mysql -u root
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.0.38-Ubuntu_0ubuntu1.1-log Ubuntu 7.04 distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> use mysql;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> update user set
    -> password=PASSWORD("NEW-ROOT-PASSWORD") where
    -> User='root';
Query OK, 3 rows affected (0.00 sec)
Rows matched: 3  Changed: 3  Warnings: 0

mysql> quit
Bye

```


# /etc/init.d/mysql stop```

 * Stopping MySQL database server mysqld                                        
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[8189]: ended
                                                                         [ OK ]
[1]+  Done                    mysqld_safe --skip-grant-tables

```

# /etc/init.d/mysql start```

 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

```
Error found here.


Continued

# mysql -u root -p
Enter password: ```

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```


Previously after accidentaly removing /home/satimis some problem popup.  Whether I need to remove mysql-server and reinstall it on repo?


B.R.
satimis

---

### Post by MJN on 2007-12-06
> Thanks for your URL. I tried it before including some other links.
 
You should've said you'd tried the usual methods otherwise it just looks like you're too lazy to seek the answer out yourself!
 
You did substitute **NEW-ROOT-PASSWORD** with your new password?
 
Mathew

---

### Post by satimis on 2007-12-06
> **MJN said:**
> You should've said you'd tried the usual methods otherwise it just looks like you're too lazy to seek the answer out yourself!
 
You did substitute **NEW-ROOT-PASSWORD** with your new password?

Hi Mathew,


I know the mistake committed previously, using password with underscore and capital "MySQL_2007".  Now problem fixed.  Thanks.


satimis

---

### Post by MJN on 2007-12-06
You've lost me, but as the problem is fixed that's all that really matters!
 
Mathew

---

