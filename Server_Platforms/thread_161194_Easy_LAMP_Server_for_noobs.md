---
title: "Easy LAMP Server for noobs"
date: 2006-04-16
forum: Server Platforms
---

### Post by spyke01 on 2006-04-16
I'm definately not the most advanced user for linux, and i wanted to make a lamp serer sandbox, so i did a search and found XAMPP which is a one stop install for 
> Apache 2.2.0, MySQL 5.0.18, PHP 5.1.1 & 4.4.1 & PEAR + SQLite 2.8.9/2.8.14 + multibyte (mbstring) support, Perl 5.8.7, ProFTPD 1.2.10, phpMyAdmin 2.7.0-pl2, OpenSSL 0.9.8a, GD 2.0.1, Freetype2 2.1.7, libjpeg 6b, libpng 1.2.7, gdbm 1.8.0, zlib 1.2.3, expat 1.2, Sablotron 1.0, libxml 2.4.26, Ming 0.2a, Webalizer 2.01, pdf class 009e, ncurses 5.8, mod_perl 2.0.1, FreeTDS 0.63, gettext 0.11.5, IMAP C-Client 2004e, OpenLDAP (client) 2.3.11, mcrypt 2.5.7, mhash 0.8.18, eAccelerator 0.9.3, cURL 7.13.1, libxslt 1.1.8, phpSQLiteAdmin 0.2, libapreq 2.06-dev, FPDF 1.53 

It installed perfectly no problem, has a good security interface, and is really easy to use. It also comes with some interesting extras, you can download it and find more information at: [http://www.apachefriends.org/en/xampp-linux.html#374](http://www.apachefriends.org/en/xampp-linux.html#374)

Hope this helps others like it has helped me.

---

### Post by mthakur2006 on 2006-04-16
Hi spyke1,
I have installed that thanx 2 u. But how do u make your website visible on it???:confused:

---

### Post by spyke01 on 2006-04-16
test it you'll have to open up a browser to , you can add your web files to /opt/lampp/htdocs and theyll be available, for you to show on the web youll have to point a domain to your ip, thats all i know though

---

### Post by ianai on 2006-04-25
Thanks for this, what a simple installation that was.:) :KS

---

### Post by adamkane on 2006-04-26
XAMPP installs a huge number of apps, and is extremely complicated to maintain. New users should start off much more simple LAMP installation.

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

---

### Post by mthakur2006 on 2006-10-21
Problem Solved :d

---

### Post by Ack99 on 2006-10-26
I was able to install everything execpt for phpmyadmin

E: Couldn't find package phpmyadmin

and I've already tried sudo apt-get update

---

### Post by az on 2006-10-26
> **Ack99 said:**
> I was able to install everything execpt for phpmyadmin

E: Couldn't find package phpmyadmin

and I've already tried sudo apt-get update

Everything excpet for phpmyadmin is in main.  Phpmyadmin is in universe.  Enable the universe repo, update and then try again.

You do not need phpmyadmin to run lamp, but you may want it.

---

