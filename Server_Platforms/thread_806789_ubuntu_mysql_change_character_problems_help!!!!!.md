---
title: "ubuntu mysql change character problems help!!!!!"
date: 2008-05-25
forum: Server Platforms
---

### Post by jackson567 on 2008-05-25
mysql version is 5.0.51a-3ubuntu5
i need to change language to utf8
i can see chinese in my phpmyadmin and mysql
but there are one problem,mysql did't save our changes
my changes:
SET NAMES utf8;
SET CHARACTER_SET_CLIENTS=utf8;
SET CHARACTER_SET_RESULT=utf8;

when i logout mysql,and login again, CHARACTER_SET_CLIENTS,connection,results change back to "latin1";


I tried in window, the mysql saved my changes, the mysql version is 5.0.27, i use chinese language on the window, but our ubuntu is use english, is it relate???

---

### Post by unutbu on 2008-05-25
Are your starting the mysql server (mysqld) 
using the --character-set-server and --collation-server options?

I don't have any direct experience with this (so the commands I suggest below may not work), but from reading the documentation in the mysql-doc package,
it appears you might want something like

```
mysqld --character-set-server=cp932 --collation-server=big5
```
or 
```

mysqld --character-set-server=cp932  --collation-server=gb2312
```

I tried to find the same info on the web, but for some reason the documentation at 
[http://dev.mysql.com/doc/refman/5.0/en/internationalization-localization.html](http://dev.mysql.com/doc/refman/5.0/en/internationalization-localization.html)
is less informative than that found in mysql-doc.
If you don't have it, I recommend installing

```
sudo apt-get install mysql-doc-5.0
```

Chapter 10 is all about Character Set Support.

---

### Post by jackson567 on 2008-05-25
> **unutbu said:**
> Are your starting the mysql server (mysqld) 
using the --character-set-server and --collation-server options?

I don't have any direct experience with this (so the commands I suggest below may not work), but from reading the documentation in the mysql-doc package,
it appears you might want something like

```
mysqld --character-set-server=cp932 --collation-server=big5
```
or 
```

mysqld --character-set-server=cp932  --collation-server=gb2312
```

I tried to find the same info on the web, but for some reason the documentation at 
[http://dev.mysql.com/doc/refman/5.0/en/internationalization-localization.html](http://dev.mysql.com/doc/refman/5.0/en/internationalization-localization.html)
is less informative than that found in mysql-doc.
If you don't have it, I recommend installing

```
sudo apt-get install mysql-doc-5.0
```

Chapter 10 is all about Character Set Support.

just installed, but where is the file locate??

---

### Post by unutbu on 2008-05-25
Index page:
file:///usr/share/doc/mysql-doc-5.0/refman-5.0-en.html-chapter/index.html

These pages might be relevant:
file:///usr/share/doc/mysql-doc-5.0/refman-5.0-en.html-chapter/charset.html (go to 10.3.1)
file:///usr/share/doc/mysql-doc-5.0/refman-5.0-en.html-chapter/charset.html#charset-asian-sets
file:///usr/share/doc/mysql-doc-5.0/refman-5.0-en.html-chapter/faqs.html#faqs-cjk
file:///usr/share/doc/mysql-doc-5.0/refman-5.0-en.html-chapter/charset.html (the chapter in general)

---

### Post by unutbu on 2008-05-25
Anytime you install a package, you can find out what files it installed this way:

```
dpkg --listfiles <package>
```

---

### Post by jackson567 on 2008-05-26
> **unutbu said:**
> Anytime you install a package, you can find out what files it installed this way:

```
dpkg --listfiles <package>
```

ahhh, need to change in my.cnf add "default-character-set=utf8"

it can work when i logout and login again, the setting is utf8, it saved, thx your information

---

