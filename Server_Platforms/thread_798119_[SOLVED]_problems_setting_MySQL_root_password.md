---
title: "[SOLVED] problems setting MySQL root password"
date: 2008-05-17
forum: Server Platforms
---

### Post by loldrup on 2008-05-17
I'm trying to install and configure MySQL on my Ubuntu 8.04 box. I found this guide in [_[COLOR="Blue"]an old thread[/COLOR]_]("http://ubuntuforums.org/forumdisplay.php?f=39"):

> **blixtra said:**
> Getting started with MySQL is really easy.  First you want to install the mysql server.  Then you can start the server with this command:

```
sudo /etc/init.d/mysql start
```

Then, because intially the root user has no password, we want to set the password like this:

```
mysqladmin -u root password myPassword
```

You can now login to the mysql server with this:

```
mysql -u root -p
```

You'll need to type in the password that you entered earlier.

Every new MySQL install has 2 databases: mysql and test.  Do NOT screw up your mysql database because here is where all the permission and user info is.  The test DB is for you to play around with.  As was mentioned earlier the MySQL documentation is excellent.  That's the main reason I prefer it over the other 2 mentioned above (maybe their docs are better nowadays.) You'll probably want to set up a new user next.


But when I get to command no. 2:
```
mysqladmin -u root password myPassword
```

it cannot connect to the server:

```
jon@jon3:~$ sudo /etc/init.d/mysql start
[sudo] password for jon: 
 * Starting MySQL database server mysqld             [ OK ] 
jon@jon3:~$ mysqladmin -u root password myPassword
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
```

What could be wrong?

---

### Post by solcott on 2008-05-17
Try doing this instead.
```

mysql -u root
UPDATE mysql.user SET Password = PASSWORD('somepassword')WHERE User = 'root';
FLUSH PRIVILEGES;

```

If the first line doesn't work, use '[FONT="Courier New"]mysql-u root -p[/FONT]' instead.

---

### Post by loldrup on 2008-05-18
Hey, that worked - thank you :D

---

