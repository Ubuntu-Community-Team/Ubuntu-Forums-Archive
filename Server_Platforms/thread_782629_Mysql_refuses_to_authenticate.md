---
title: "Mysql refuses to authenticate"
date: 2008-05-05
forum: Server Platforms
---

### Post by turbulenceau on 2008-05-05
Hi All,

I've just installed Mysql version 5 onto my Ubuntu 7.10 Gutsy server.

I did this by using apt-get
*sudo apt-get install mysql-server-5.0*

It prompted me for a root password (which I set as "password") and completed the install.

Now, when I attempt to connect (using the password I set when installing mysql) I get the following error:
**ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)**

I simply can not make it authenticate. I even went as far as uninstalling mysql and reinstalling and leaving the admin password as blank, but that also does not work.

Does anyone have any ideas as to what the problem might be?

Thanks in advance,
Cheers

---

### Post by madhusudancs on 2008-05-05
Hey this is simple, while running mysql give the command like this

```
$ mysql -u root -p 
```

This promopts you for mysql password which you enter and you must be able to login.

---

### Post by turbulenceau on 2008-05-05
Thanks but that is the problem I have

Any other ideas??

root@server:~# mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
root@server:~#

---

### Post by azzamite on 2008-05-05
If it's the first time you install it, then make shure
mysql is being executed at startup or init it yourself.

Also make shure you ran mysql_secure_installation, from
there you can (dis)allow  root/anonimous local/remote login.

---

### Post by madhusudancs on 2008-05-05
> **turbulenceau said:**
> 
root@server:~# mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
root@server:~#

This problem should occur only if the password is incorrect. Please try resetting your password by following the procedure given below

[LIST=1]Stop the MySQL Server.
```
$ sudo /etc/init.d/mysql stop
```

[*]Start the mysqld configuration.
```
$ sudo mysqld --skip-grant-tables &
```


[*]Login to MySQL as root.
```
$ mysql -u root mysql
```

[*]Replace YOURNEWPASSWORD with your new password!
```
UPDATE user SET Password=PASSWORD('YOURNEWPASSWORD') WHERE User='root'; FLUSH PRIVILEGES; exit;
```

[*]Start the MySQL Server again.
```
$ sudo /etc/init.d/mysql start
```
[/LIST]
You can also use this tutorial 

[https://help.ubuntu.com/community/MysqlPasswordReset]("https://help.ubuntu.com/community/MysqlPasswordReset")

---

