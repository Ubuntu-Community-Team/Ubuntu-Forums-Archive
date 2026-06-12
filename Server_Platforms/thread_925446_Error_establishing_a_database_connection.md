---
title: "Error establishing a database connection"
date: 2008-09-20
forum: Server Platforms
---

### Post by jamelb on 2008-09-20
So my hard drive died and i lost everything. I got my server back up and running in about an hour. All works perfect except i can not seem to install wordpress again. I get this

Error establishing a database connection

This either means that the username and password information in your wp-config.php file is incorrect or we can't contact the database server at localhost. This could mean your host's database server is down.

    * Are you sure you have the correct username and password?
    * Are you sure that you have typed the correct hostname?
    * Are you sure that the database server is running?

If you're unsure what these terms mean you should probably contact your host. If you still need help you can always visit the WordPress Support Forums.

now i has double checked everything and all the information in the wp-config.php is correct. I have no idea what could be wrong. I use webmin to control my mysql database. Any help would be great.

---

### Post by cariboo on 2008-09-20
Can you access mysql in a console using the user name and password you set up?

```
mysql -u <username> -p
```

where <username> is your user name and you will be prompted for a password.

Jim

---

### Post by jamelb on 2008-09-20
ERROR 1045 (28000): Access denied for user 'blog'@'localhost' (using password: YES)

is what i get

---

### Post by cariboo on 2008-09-21
The first thing to check, is to make sure mysql is running:

```
ps ax | grep mysql
```

should output something like this:

```
 ps ax | grep mysql
 9686 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
 9807 ?        Sl     0:01 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
 9808 ?        S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
 9850 pts/1    S+     0:00 grep mysql
```

Next, when you setup wordpress, did you use root as your database user name or another user name.

If you used root and still can't run mysql, you could try reconfiguring mysql and entering a new password for root:

```
dpkg-reconfigure mysql-server-5.0
```

I don't like using root for accessing mysql. I always create a user with my user name to do anything with mysql:

```
mysql> grant all privileges on *.* to user@'localhost'
    -> identified by 'password' with grant option;
Query OK, 0 rows affected (0.06 sec)

mysql> grant all privileges on *.* to user@'%'
    -> identified by 'password' with grant option;
Query OK, 0 rows affected (0.00 sec)
```

I've edited out my user name and password. Another advantage of setting up a user this way, is that you can remotely access the database without having to set up a host in mysql.

Jim

---

