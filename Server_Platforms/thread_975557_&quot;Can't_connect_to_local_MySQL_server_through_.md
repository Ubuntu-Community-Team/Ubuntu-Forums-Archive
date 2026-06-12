---
title: "&quot;Can't connect to local MySQL server through socket&quot;"
date: 2008-11-08
forum: Server Platforms
---

### Post by kami_iwinaru on 2008-11-08
I'm setting up a mail server with 7.10, following the directions on this website: [http://flurdy.com/docs/postfix/#install]("http://flurdy.com/docs/postfix/#install"). I'm at the part where you create the mysql database. So when I put in the command ```
mysqladmin -u root password *new_password*
``` it tells me this: ```
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

``` How do I create the mysqld.sock?

---

### Post by unutbu on 2008-11-08
First check that mysqld is installed:
```

which mysqld
```
This should return 
```
/usr/sbin/mysqld
```
Next check that mysqld is running:
```
pgrep mysqld
```
This should return a line(s) with a number(s). This in the process id number (PID).
If you don't see any number, then check that mysql is set to start when you boot up:
```
ls /etc/rc2.d | grep mysql
```
You should see
```
S17mysql-ndb-mgm
S18mysql-ndb
S19mysql
```
If you see this, reboot, and mysqld should run and /var/run/mysqld/mysqld.sock should be created for at boot time.

If you don't see the output described above, then post the commands and their output and we'll go from there.

---

### Post by kami_iwinaru on 2008-11-08
I had to reboot. So now when I enter ```
pgrep mysqld
``` it returns with ```
6406
6446

```
So after that I tried ```
mysqladmin -u root password *new_password*
``` again. Now it tells me ```
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

```
I'm already in root. So I don't think that's the case.

---

### Post by cariboo on 2008-11-08
when start mysql you have to use the password you set when you installed it.

```
mysql -u root -p
```

should result in this after you enter your password:

```
 mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 407
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>
```

Jim

---

### Post by kami_iwinaru on 2008-11-08
```
root@server:/home/kami# mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
```

I've tried everything that I used. Is there a way to reset it all?

And just to make sure I'm doing this right, the code is 
```
mysqladmin -u root password *password_i_choose*
```

Correct?

---

### Post by unutbu on 2008-11-08
kami_iwinaru, what happens when you type
```
mysql -u root
```
If you get a mysql> prompt, then type
```

GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' IDENTIFIED BY 'yourpassword' WITH GRANT OPTION; 
```

Change yourpassword to whatever you wish.
Keep the single quotes, they are part of the command.

If, on the other hand, the above command does not get you to a mysql> prompt, then do this:

```
sudo /etc/init.d/mysql stop
sudo mysqld --skip-grant-tables &
mysql -u root
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' IDENTIFIED BY 'yourpassword' WITH GRANT OPTION; 
mysql>flush privileges
mysql>quit
sudo killall mysqld
sudo /etc/init.d/mysql start
```

This will allow you to (re)set your mysql root password. You can also skip to ```

mysqladmin -u root password password_i_choose
```
command. If you'd like to check that mysqladmin works, however, do this:

```
mysqladmin -u root -p version
```
You should see some innocuous version info.

When prompted for a password, type in your mysql root password.

Note that once a mysql root password has been set, 
you must always use the -p flag when using the mysql or mysqladmin commands. The -p flag tells the program to prompt for a password.

Your mysql root password is a completely different thing than your Ubuntu password(s). For security's sake, they should be different passwords.

---

### Post by kami_iwinaru on 2008-11-08
The "mysql -u root" command didn't work the first time. So I did the
```
sudo /etc/init.d/mysql stop
```
That stopped fine, but when I entered 
```
sudo mysqld --skip-grant-tables
```
it comes up with 
```
081108 21:51:16  InnoDB: Started; log sequence number 0 43655
081108 21:51:17 [Note] mysqld: ready for connections.
Version: '5.0.45-Debian_1ubuntu3-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Debian etch distribution
```
and after that, it just stops. Doesn't do anything. I left it there for a good 10 minutes and still nothing. So that's where I'm stuck.

---

### Post by unutbu on 2008-11-08
Sorry, I forget to put a & after the command.
```
sudo mysqld --skip-grant-tables &
```

---

### Post by kami_iwinaru on 2008-11-08
Still did the same thing. Someone told me to use phpMyAdmin. But I tried it, and it's confusing the hell out of me, so I think I'd rather do this.

---

### Post by unutbu on 2008-11-08
Type
```
sudo mysqld --skip-grant-tables &
```

Then press return. You should get a prompt back.

---

### Post by kami_iwinaru on 2008-11-08
OK, that one part worked. Now for the next problem. >_<
```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' IDENTIFIED BY 'mypassword' WITH GRANT OPTION;
ERROR 1290 (HY000): The MySQL server is running with the --skip-grant-tables option so it cannot execute this statement

```
That's what happens next.

---

### Post by unutbu on 2008-11-08
At the mysql> prompt, what do you get when you type this:

```

use mysql;
select user,host,password from user where user='root';

``` (Of course, do not post your password, but I would be interested to know if it is blank.)
Do you get something like this?
```

+------+-------------+-------------------------------------------+
| user | host        | password                                  |
+------+-------------+-------------------------------------------+
| root | localhost   | *XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX | 
+------+-------------+-------------------------------------------+

```
If so, type```

update user set Password=Password('newpassword') where user='root';
```

---

### Post by cariboo on 2008-11-09
If worse comes to worse you can always run:

```
sudo dpkg-reconfigure mysql-server-5.0
```

and create a new password for the mysql root user.

Jim

---

