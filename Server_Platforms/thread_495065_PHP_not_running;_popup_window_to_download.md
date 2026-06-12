---
title: "PHP not running; popup window to download?"
date: 2007-07-07
forum: Server Platforms
---

### Post by gargo2000 on 2007-07-07
I have installed Apache, Mysql, PHP5.  This was working the other day and I dont know what I did, but tried to start from scratch and removed all 3 then reinstalled them.  I'm still getting that darn windows to download a PHP file instead of running the script.  Please Help!

Thanks!

---

### Post by Alterax on 2007-07-07
sudo apt-get install php5-apache2-mod-bt php5-cgi php5-common php5-curl php5-gd php5-mysql

then restart Apache2:

sudo /etc/init.d/apache2 restart

Then in your root webserver directory make a test.php file with this line in it.

<?php phpinfo() ?>

Now browse to that file using a web browser (i.e., [http://localhost/test.php](http://localhost/test.php) )
If it is working right it should give information on your PHP installation.
NOTE:  If you are trying to open the file, you have to go through the url to it above.  If you just navigate to it and click to open, you'll just get the source.  Apache2 has to do the conversion of PHP to HTML on the fly.

--Alterax

---

### Post by Alterax on 2007-07-07
Also install either libapache2-mod-php5 or libapache-mod-php5 .  For the ones above, if you are using apache instead of apache2, just drop the 2 and it should work.

Enjoy!

--Alterax

---

### Post by gargo2000 on 2007-07-07
> **Alterax said:**
> sudo apt-get install php5-apache2-mod-bt php5-cgi php5-common php5-curl php5-gd php5-mysql

--Alterax

the php5-apache2-mod-bt doesn't exist

---

### Post by gargo2000 on 2007-07-07
One other thing in my search all day...I came across this:

sudo a2enmod php5 
This module does not exist!

To me this sounds like it may be the issue I'm having

---

### Post by ntom-taylor on 2007-07-11
I know you've probably tried it to death, but i recently wrote a big 'how to' where i tried to be as comprehensive as possibly in installign all the major web server apps for your ubuntu. 

You can find it by [clicking here]("http://www.theatons.com/blog/2007/07/01/ubuntu-install-php5-mysql-apache2-ssl-pdo-pdo_mysql/")

I also encountered you problem before, and found a solution by making sure libapache2-mod-php5 is installed (as has been said before), but there was also another solution somthing todo with forcing the apache2 to read php files as php, it on the forum somewhere.

Hope it helps
Tom

---

### Post by az on 2007-07-11
> **gargo2000 said:**
> I have installed Apache, Mysql, PHP5.  This was working the other day and I dont know what I did, but tried to start from scratch and removed all 3 then reinstalled them.  I'm still getting that darn windows to download a PHP file instead of running the script.  Please Help!

Thanks!

What apache packages do you have installed?  What php packages?


dpkg -l |grep apache
dpkg -l|grep php

See here:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

The LAMP packages to install are:
apache2 php5-mysql libapache2-mod-php5 mysql-server
and that will get you the whole stack.  Sometimes, then you install them seperately, you can end up installing conflicting versions of some package.  That's why your apache doesn't think php is available.

---

### Post by bwakkie on 2008-06-26
I had the same and I found that php5.load isn't linked correctly after install. At least in 8.04 Hardy not.

cd /etc/apache2/mods-enabled
sudo ln -s ../mods-available/php5.load
sudo /etc/init.d/apache2 restart


Cheers

---

