---
title: "Re-compile PHP 5 w/MySQL support?"
date: 2009-10-05
forum: Server Platforms
---

### Post by FlyboyData on 2009-10-05
Hello, I downloaded the server build of Jaunty Jackalope to try and quickly bring up a LAMP server to run a specific, already-developed *AMP web app.
 
However, it was quickly apparent that the default distro version of PHP 5.2.6 didn't contain all of the features that our app requires.
 
I first downloaded the PHP5.2.6 source package using apt-get, however I found some "irregularities" with the distro source as compared to the PHP 5.2.6 source distro (such as the dbase source code tree being empty-not a big deal to many users, unfortunately our *AMP app requires this ancient database support to support legacy database uploads...). So then, I went to php.net, and downloaded the 5.2.6 source instead.
 
I then added all the intermediate ubuntu packages I needed to make ./configure work without complaints, and successfully compiled PHP with all of the libraries we needed (dbase, gd, ftp, and zip).
 
However, a phpinfo() on the recompiled PHP5 reveals that MySQL and MySQLi support didn't make the cut somehow...despite a distinct lack of complaints from the PHP configure commands, and the make and make install commands. Grrr....
 
I suspect the problem may be in the directory that I am pointing the configuration script to (/usr, as best as I can tell...).
 
Here is the ./configure command line that I used... (taken from phpinfo(), so please excuse the extraneous single quotes :P )
 
'./configure' '--with-apxs2=/usr/bin/apxs2' '--enable-dbase' '--with-config-file-path=/etc/php5/apache2' '--with-mysql=shared,/usr' '--with-mysqli=shared,/usr/bin/mysql_config' '--with-gd' '--with-bz2' '--with-zlib' '--enable-mbstring' '--enable-calendar' '--enable-bcmath' '--enable-ftp' '--enable-exif' '--enable-zip' 
 
Anyone know how to configure PHP5 with MySQL and MySQLi support?

---

### Post by cdenley on 2009-10-05
> **FlyboyData said:**
> 
Anyone know how to configure PHP5 with MySQL and MySQLi support?

```

sudo apt-get install php5-mysql

```

I think the precompiled package should work with a user-compiled php5 base. If not, if you compiled php the ubuntu way, it should have generated the php5-mysql package.

---

### Post by FlyboyData on 2009-10-05
>  Code:
sudo apt-get install php5-mysql
 
No dice, here's what I got when I tried that...
 
```
[EMAIL="root@linus:/home/bboswell"]root@linus:/home/bboswell[/EMAIL]# apt-get install php5-mysql
Reading package lists... Done
Building dependency tree
Reading state information... Done
php5-mysql is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 53 not upgraded.
[EMAIL="root@linus:/home/bboswell#"]root@linus:/home/bboswell#[/EMAIL]
``` 
 
I know that I'm definitely a noobie at ubuntu...
 
>  If not, if you compiled php the ubuntu way, it should have generated the php5-mysql package.

 
Care to give me an education on what the ubuntu way is?  A link to the FM that I didn't read will work, too...;)

---

### Post by cdenley on 2009-10-05
> **FlyboyData said:**
> Care to give me an education on what the ubuntu way is?  A link to the FM that I didn't read will work, too...;)

I don't have any links handy, but it involves
```

sudo apt-get source php5
sudo apt-get build-dep php5

```
then a debuild command, using the options from the example in the manual. That will build the packages from source. That would give you packages identical to the ones in the repo's, except you can tweak the configuration before compiling as needed. If you compiled it from scratch, it probably isn't look for the mysql library from the repo in the right place.

---

### Post by wojox on 2009-10-05
'--with-mysql=shared,/usr' '--with-mysqli=shared,/usr/bin/mysql_config' Why the shared? Shouldn't it be just the directory?

---

### Post by FlyboyData on 2009-11-17
Okay,

Mistake #1: you are right, Ubuntu's default MySQL5 distribution is not compiled as a shared module(!).  So, this build statement fixed it:

'./configure' '--with-apxs2=/usr/bin/apxs2' '--enable-dbase' '--with-mysql=/usr/bin' '--with-mysqli=/usr/bin/mysql_config' '--with-gd' '--with-bz2' '--with-zlib' '--enable-mbstring' '--enable-calendar' '--enable-bcmath' '--enable-ftp' '--enable-exif' '--enable-zip' '--enable-gd-native-ttf' '--with-ttf' '--with-freetype-dir=/usr/include/freetype' '--with-xpm-dir=/usr/lib' '--with-mysql-sock=/var/run/mysqld/mysqld.sock'

The mysql-sock option pointing to the mysql socket file specified in my.cnf also helped things immenseley...

:P

---

