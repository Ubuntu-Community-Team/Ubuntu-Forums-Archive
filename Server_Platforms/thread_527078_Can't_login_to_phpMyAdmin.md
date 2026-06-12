---
title: "Can't login to phpMyAdmin"
date: 2007-08-16
forum: Server Platforms
---

### Post by Dingbats on 2007-08-16
I have just installed Apache, PHP and MySQL on my 7.04 system. Everything seems to work fine, except that I can't find out how to log in to phpMyAdmin. I have set a root password from the mysql prompt with

```
SET PASSWORD FOR 'root'@'localhost' = PASSWORD('password');
```

But I can't log in with the username 'root' and its password from the phpMyAdmin login prompt, nor with a blank password. My php scripts can connect just fine to the database, as root. I have restarted Apache several time but it hasn't changed anything.

It's probably something obvious, but what is it I should do? :/

---

### Post by KevinM1 on 2007-08-16
> **Dingbats said:**
> I have just installed Apache, PHP and MySQL on my 7.04 system. Everything seems to work fine, except that I can't find out how to log in to phpMyAdmin. I have set a root password from the mysql prompt with

```
SET PASSWORD FOR 'root'@'localhost' = PASSWORD('password');
```

But I can't log in with the username 'root' and its password from the phpMyAdmin login prompt, nor with a blank password. My php scripts can connect just fine to the database, as root. I have restarted Apache several time but it hasn't changed anything.

It's probably something obvious, but what is it I should do? :/

I was having some phpMyAdmin login problems myself not too long ago.  I would enter in the correct login info, but it would take about 10 tries before it would accept it.  For some reason, installing PHP's mcrypt package fixed the problem.  If you don't have that package, try installing it and see if that fixes the problem.

---

### Post by Dingbats on 2007-08-16
Installed mcrypt, but it didn't change anything. I still says:

> Error
#1045 - Access denied for user 'www-data'@'localhost' (using password: YES)

Even though I log in with the username "root".

---

### Post by UbuntuniX on 2007-08-16
> **KevinM1 said:**
> I was having some phpMyAdmin login problems myself not too long ago.  I would enter in the correct login info, but it would take about 10 tries before it would accept it.  For some reason, installing PHP's mcrypt package fixed the problem.  If you don't have that package, try installing it and see if that fixes the problem.

That bug was fixed.

---

### Post by KevinM1 on 2007-08-16
> **UbuntuniX said:**
> That bug was fixed.

Nice.  Is there an easy way to update/upgrade my phpMyAdmin without having to redo my installation?

---

### Post by Dingbats on 2007-08-17
Anyway, are there any solutions to my problem?

---

### Post by Dingbats on 2007-08-20
Bump...:(

---

### Post by southernman on 2007-08-20
[http://www.google.com/search?q=error+1045&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a]("http://www.google.com/search?q=error+1045&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")

---

### Post by Dingbats on 2007-08-21
Thanks. I found [this]("http://forums.mysql.com/read.php?11,34014,46593") which seems to be helpful, but I don't know how I would stop the mysql server, so I can start it again with the --skip-grant-tables option. ?

---

### Post by Dingbats on 2007-08-21
Uhm... I really don't get it. I don't know how to start and stop the mysql server (I have googled).

---

### Post by southernman on 2007-08-21
The way I did it was simply:

/etc/init.d/mysql restart

when it shut down, it gave the error but on start up, it didn't.

---

### Post by Dingbats on 2007-08-21
> **southernman said:**
> The way I did it was simply:

/etc/init.d/mysql restart

when it shut down, it gave the error but on start up, it didn't.

When I run that I get:

```
open: Permission denied
 * Stopping MySQL database server mysqld                                        open: Permission denied
                                                                         [ OK ]
open: Permission denied
 * Starting MySQL database server mysqld                                        open: Permission denied
                                                                         [fail]

```

---

### Post by southernman on 2007-08-21
lol sorry I shouldn't assume anything - do this instead:

sudo /etc/init.d/mysql restart

---

### Post by Dingbats on 2007-08-21
That works. But when I log in to mysql from the terminal, and type

```
mysql> UPDATE user SET Password=PASSWORD('your_new_password') where USER='root'; 
```

I get:

```
ERROR 1046 (3D000): No database selected

```

:confused:

I apologise for being such a noob, I actually thought I would be better at this than I was...

---

### Post by WhosRodney on 2007-08-28
You need to tell mysql what database you are using.  Try

```
mysql> USE mysql;
```

:)

---

