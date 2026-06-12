---
title: "How to activate SQLite?"
date: 2012-03-22
forum: Server Platforms
---

### Post by jrohde on 2012-03-22
Hi

I'm trying to install EyeOS on Ubuntu Server 11:10. Only unfulfilled prerequisite is the SQLite Extension. If I do a 

```
sudo apt-get install php5-sqlite
``` 

I'm told that it's already installed. And I have checked the /etc/php5/apache2/php.ini and the /etc/php5/conf.d/sqlite.ini which are both ok.

Why does EyeOS keep telling me that SQLite is not activated?

Thanks
JRohde

---

### Post by Cheesemill on 2012-03-22
Have you actually got sqlite installed as well as the php extension?

---

### Post by jrohde on 2012-03-22
Hi Cheesemill

Well, now I have... And it doesn't change anything.

JRohde

---

### Post by d4m1r on 2012-03-23
How did you install SQLite? Also, do you have Apache/PHP/MySQL setup on the machine?

---

### Post by jrohde on 2012-03-23
I have a fully functional server running Ubuntu Server 11.10 and Samba, Apache, MySQL, PHP5 etc. running fine. I installed SQLite with:

```
sudo apt-get install sqlite
```

/JRohde

---

### Post by dharmavir on 2012-03-24
Hi jrohde,

$ sudo apt-get install php5-cli php5-dev make
$ sudo apt-get install libsqlite3-0 libsqlite3-dev
$ sudo apt-get install php5-sqlite3
$ sudo apt-get remove php5-sqlite3
$ cd ~
$ wget [http://pecl.php.net/get/sqlite3-0.6.tgz](http://pecl.php.net/get/sqlite3-0.6.tgz)
$ tar -zxf sqlite3-0.6.tgz
$ cd sqlite3-0.6/
$ sudo phpize
$ sudo ./configure
$ sudo make
$ sudo make install
$ sudo apache2ctl restart

Basically installing simply sqlite won't do anything if you want to use it with php, you must install php-plug (I mean extension) for that to make it work with it.

I hope this helps: (ripped from below url)
[http://stackoverflow.com/questions/948899/how-to-enable-sqlite3-for-php](http://stackoverflow.com/questions/948899/how-to-enable-sqlite3-for-php)

---

### Post by jrohde on 2012-03-26
Hi dharmavir

I did what you suggested, but "sudo make" gave me a lot of lines with:

~/sqlite3-0.6/sqlite3.c:<xxxx>:1: error: duplicate 'static'

The previous commands worked fine.

Do you know the cause of this error?

JRohde

---

