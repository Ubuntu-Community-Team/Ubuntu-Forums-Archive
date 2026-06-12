---
title: "php cant recognize mysql"
date: 2005-11-05
forum: Server Platforms
---

### Post by ededdede on 2005-11-05
Hi new user, new poster, setting up ubuntu 5.10 as a webserver.

I followed the instructions here [https://wiki.ubuntu.com/ApacheMySQLPHP]("https://wiki.ubuntu.com/ApacheMySQLPHP") to set mysql and php up.

Went here [http://dev.mysql.com/doc/refman/5.0/en/starting-server.html]("http://dev.mysql.com/doc/refman/5.0/en/starting-server.html") to get mysql working.

php works, but when i try  mysql_connect() in a php file, it gives back 

Fatal error: Call to undefined function mysql_connect() in /var/www/mysql_connect.php on line 9

Am I missing something here? Sorry if this has been answered 5000 times before

edit:
Oh yeah It's PHP5, not PHP4. Besides that I followed the instructions exactly

edit 2:
Oh yeah MySQL works. I can log in and change my databases. I have MySQLadmin installed which also works.

---

### Post by suRoot on 2005-11-05
You need to install the php-mysql package

```
sudo apt-get install php5-mysql
```

---

### Post by ededdede on 2005-11-05
I did that already.. tried again said that php5-mysql is already the newest version... :confused:

---

### Post by MakubeX on 2005-11-05
maybe you can post the php code here.. it might be a syntax error?

The packages that I had installed (provided that Apache2 was installed before) were:

```
Installed the following packages:
libapache2-mod-auth-mysql (4.3.9-2ubuntu1)
libapache2-mod-perl2 (2.0.1-3)
libapache2-mod-python (3.1.3-3ubuntu1)
libapache2-mod-python-doc (3.1.3-3ubuntu1)
libapache2-mod-python2.4 (3.1.3-3ubuntu1)
libdevel-symdump-perl (2.03-3)
libhtml-parser-perl (3.45-2)
libhtml-tagset-perl (3.04-1)
libhtml-tree-perl (3.18-1)
liburi-perl (1.35-1)
libwww-perl (5.803-4)

apache2-doc (2.0.54-5ubuntu2)

apache-common (1.3.33-8)
libapache-mod-php4 (4:4.4.0-3)
libzzip-0-12 (0.12.83-5)
php4-common (4:4.4.0-3)
php4-mysql (4:4.4.0-3)
php5-mysql (5.0.5-2ubuntu1)

libdbd-mysql-perl (2.9007-1)
libdbi-perl (1.48-1)
liblockfile1 (1.06)
libmysqlclient12-dev (4.0.24-10ubuntu2)
libnet-daemon-perl (0.38-1)
libplrpc-perl (0.2017-1)
mailx (1:8.1.2-0.20040524cvs-4ubuntu1)
mysql-client (4.0.24-10ubuntu2)
mysql-server (4.0.24-10ubuntu2)
postfix (2.2.4-1ubuntu2)
```

---

### Post by ededdede on 2005-11-05
Here is what I have so far:

```

<?php

#Defining user, pw, host, name here

$link = mysql_connect( DBHOST, DB_USER, DB_PASSWORD);
if($link){
    die( mysql_error());
}
@mysql_select_db (DB_NAME) OR die mysql_errore());

?>


```

It throws the error on the mysql_connect() function.



How can I get a list of what packages I have installed?

That way I could just run down that list you wrote and see what I am missing.

---

### Post by linuxbz on 2005-11-05
[QUOTE=ededdede]Here is what I have so far:
```

#Defining user, pw, host, name here

```
[/QUOTE]

Use '//' for comments in PHP, not '#'.

For a block comment, use '/*' to start and '*/' to end.

[QUOTE=ededdede]
```

$link = mysql_connect( DBHOST, DB_USER, DB_PASSWORD);
if($link){
    die( mysql_error());
}
@mysql_select_db (DB_NAME) OR die mysql_errore());

```
[/QUOTE]

You need actual literal or variable values here, not bare words. At least in PHP4, it would be something like:

```

$link =mysql_connect( 'localhost', 'user1', 'user1passwd' );

```

Often those would be replaced with variables, but the strings they
resolve to must be the ones MySQL expects as an authorized user.

Hope this helps.

---

### Post by ededdede on 2005-11-05
[QUOTE=linuxbz]Use '//' for comments in PHP, not '#'.

[/QUOTE]

I don't really have that part commented out. That is just where I used DEFINE to make static variables DB_USER, DB_PASSWORD.

So I have 
```

DEFINE ('DB_HOST', 'localhost:3306');

```
for one of my variables.


Would it be easier if I just installed Ubuntu server?

Sigh I should format and install Server 2000.

---

### Post by ededdede on 2005-11-05
[QUOTE=MakubeX]maybe you can post the php code here.. it might be a syntax error?

The packages that I had installed (provided that Apache2 was installed before) were:

.......

[/QUOTE]


Ok I went though and made sure I had all those installed and updated. Still not working.. :confused: 

Oh and I actually have 5.10 Preview installed on this... could that be the cause of all this problem?

---

### Post by LordHunter317 on 2005-11-06
[QUOTE=linuxbz]You need actual literal or variable values here, not bare words. At least in PHP4, it would be something like:[/quote]They very well could have been constants with those names.

The issue cannot possible be with his script anyway, the error message makes that clear.

Chances are your php.ini doesn't have 'extension=mysql.so' uncommented, so thats' the first thing I'd check.  Make sure to restart apache after changing it.

---

