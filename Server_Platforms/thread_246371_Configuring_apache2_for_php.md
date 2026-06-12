---
title: "Configuring apache2 for php"
date: 2006-08-29
forum: Server Platforms
---

### Post by geminias on 2006-08-29
Hello i'm dealing with a fresh install of unbuntu server and don't know if php is even installed.  Its the latest version of ubuntu server so i hope php is already installed.  

Also, once installed, how do I configure apache2 to use .php extensions.  Thanks.

---

### Post by Kurt` on 2006-08-29
Make a .php file and put <?php phpinfo(); ?> in it. Visit it in your browser, see if it shows that text, or a PHP info page. ;)

As for configuring it... you don't even have to. Assuming it's NOT installed, just run

# sudo apt-get install libapache2-mod-php4

then

# sudo /etc/init.d/apache2 reload

---

### Post by geminias on 2006-08-29
well, whenever i try to use a .php file it asks me to download it.  Thats how i know apache can't be configured to use .php extensions.  There's a line in a config file i have to change to add it.  Right?

---

### Post by az on 2006-08-29
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


If you use apache2, php5 and mysql provided in the default LAMP in Ubuntu, everything is already configured for you.

Unless you picked the LAMP install when you installed your server, you neeed to install the LAMP stack yourself:

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server


All those packages are in main and on the server cd.  Php4 is in universe and is not always as well configured as php5.  See the howto on the wiki.

---

### Post by jimm on 2006-08-29
Hi geminias,

In your Apache.conf file make sure the following line is not commented and/or exists or you have a php5.conf (or 4 or both!) file in your apache/mods-enabled directory that contains the same directive:

AddType application/x-httpd-php .php

If you want PHP4 and PHP5 to work together here are the packages I installed to get everything working:

apt-get php5 php4-cgi libapache2-mod-php5 php4-cgi 

This should put all the config files and stuff in the right place (/etc/php/apache2 ...) 

Then you need to restart Apache2 and you should be all go!

Another tip... Make sure you clear your browser cache before you retry loading the .php page. I had the same problem you did and couldnt figure it out, Firefox had the page in the cache and kept telling me to download rather than displaying the page. Once I did the above config changes and installs and cleared my browser cache it came right.

Hope that helps!

Thanks,
James

---

### Post by geminias on 2006-08-29
Right on Jimm.  That was why it wasn't working.  The damn firefox cache lol.  That tip probably saved me years, if not milleniums of time.  Thanks bro.

---

### Post by jimm on 2006-08-29
No Worries! Glad it worked out... Its like bangin ya head against a wall with these things sometimes :-)

---

### Post by ruza on 2007-11-25
Hello! I do not want to start new theme because my problem is related to apache and php... I would like to use website baker so i need an active server... I know how to do that using win but i do not want to think about using win... How to do that?

---

### Post by mellowd on 2007-11-25
> **ruza said:**
> Hello! I do not want to start new theme because my problem is related to apache and php... I would like to use website baker so i need an active server... I know how to do that using win but i do not want to think about using win... How to do that?

What exactly are you asking? How to get a linux server online, how to just get some space on an already online linux server? What exactly?

---

### Post by ruza on 2007-11-25
> **mellowd said:**
> What exactly are you asking? How to get a linux server online, how to just get some space on an already online linux server? What exactly?

Well I need to install wb but i dont know where. In win I could just unpack it to m:\www folder(localhost/www)... But I do not know how to acces localhost now. And I need to create a database for that site to use and i dont know how...

---

### Post by mellowd on 2007-11-25
Have you looked at Web Bakers web page? There is an install routine right over  here: [http://help.websitebaker.org/pages/en/basic-docu/installation/wb-installer.php](http://help.websitebaker.org/pages/en/basic-docu/installation/wb-installer.php)

---

### Post by ruza on 2007-11-25
> **mellowd said:**
> Have you looked at Web Bakers web page? There is an install routine right over  here: [http://help.websitebaker.org/pages/en/basic-docu/installation/wb-installer.php](http://help.websitebaker.org/pages/en/basic-docu/installation/wb-installer.php)

Yes but they dont say how to upload files to webserver... And i cant upload them to localhost... And is there an easy way to setup database something like uniserver for win (something like gui for databases)?

---

### Post by ruza on 2007-11-25
Step 2: Pre-Installation Checks

   1. On your server, create the directory where you want to install WB.
   2. Make sure you have permission to read & write to this directory via ftp. To confirm, you can use your ftp client to try accessing, uploading and deleting a file there.
   3. Create a MySQL database and a database user for your new site. Make sure the user has proper permission for adding and deleting both entries and tables in the database. Make a note of the database name, the user and password.
 
How to do all that?

---

### Post by mellowd on 2007-11-25
Do you have any experience on the linux command line at all?

---

### Post by ruza on 2007-11-25
> **mellowd said:**
> Do you have any experience on the linux command line at all?

Yes i have... But I dont have any exp in website making...

---

### Post by mellowd on 2007-11-25
> **ruza said:**
> Yes i have... But I dont have any exp in website making...

Fari enough, but the 3 steps you mentioned can all be done on the command line. Are you sure you know how to use it?

---

### Post by ruza on 2007-11-25
> **mellowd said:**
> Fari enough, but the 3 steps you mentioned can all be done on the command line. Are you sure you know how to use it?

But how... I cant even access localhost except with firefox...

---

### Post by mellowd on 2007-11-25
> **ruza said:**
> But how... I cant even access localhost except with firefox...

Do you know that localhost is your own pc?

---

### Post by ruza on 2007-11-25
> **mellowd said:**
> Do you know that localhost is your own pc?

Yes but still I thought that localhost has to be virtual partition like in win. Does that mean that i can install wb anywhere? Or I need to do it on / ? And what can i do about that database?

---

### Post by mellowd on 2007-11-25
> **ruza said:**
> Yes but still I thought that localhost has to be virtual partition like in win. Does that mean that i can install wb anywhere? Or I need to do it on / ? And what can i do about that database?

Do you have apache installed? If so, the root of your "web" will be here ---> /var/www

---

### Post by ruza on 2007-11-25
> **mellowd said:**
> Do you have apache installed? If so, the root of your "web" will be here ---> /var/www

That was what I neaded!!! Thank you! And what about database? Is there any user-friendly(read: made for idiots) gui for making databases?

---

### Post by mellowd on 2007-11-25
> **ruza said:**
> That was what I neaded!!! Thank you! And what about database? Is there any user-friendly(read: made for idiots) gui for making databases?

There is but I haven't used it myself, you can find it here: [http://dev.mysql.com/downloads/gui-tools/5.0.html](http://dev.mysql.com/downloads/gui-tools/5.0.html)

---

### Post by ruza on 2007-11-25
> **mellowd said:**
> There is but I haven't used it myself, you can find it here: [http://dev.mysql.com/downloads/gui-tools/5.0.html](http://dev.mysql.com/downloads/gui-tools/5.0.html)

There is one more problem... i could setup database using wb but I am not allowed to create database on my computer... It says permis. denied to user ruza....What to do? Should i delete some config folder or...?

---

### Post by ruza on 2007-11-25
Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'root'@'localhost' (using password: NO) in /var/www/install/save.php on line 345 

Changing username does not help... And he does not remember my pass(when I use it)...

---

### Post by mellowd on 2007-11-25
have you sudo'd ?

---

### Post by ruza on 2007-11-25
> **mellowd said:**
> have you sudo'd ?

Yep... usrname is root.. I have tried with and without pass...

---

### Post by ruza on 2007-11-25
Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'root'@'localhost' (using password: YES) in /var/www/install/save.php on line 345

Warning: Cannot modify header information - headers already sent by (output started at /var/www/install/save.php:345) in /var/www/install/save.php on line 80

---

### Post by ruza on 2007-11-25
How do i configure mysql?

---

### Post by mellowd on 2007-11-25
Try this:

```
mysql -u root -p
```

then enter your mysql root password

---

### Post by ruza on 2007-11-25
ruza@Desktop:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

---

### Post by mellowd on 2007-11-25
Are you sure you're got the right password? When you installed mysql did you specify a mysql password? It will be different to your root password

---

### Post by ruza on 2007-11-25
Yes I know that... I specified a pass other than my root pass but I dont get it... I did that today so there is no way i could forget it... And I would like to change it...

---

### Post by ruza on 2007-11-25
Nothing helped... Does anyone know how to reconfigure mysql?

---

### Post by arjenlodder on 2007-11-25
Hello, 
I have installed apache2 and PHP5 and MySql... The whole packet.
But it downloads the PHP files... It isn'my firefox cache (i emptyd it, and IE doesn't work too).
I've also done a2enmod php5, it says that the module is already installed.
Who can i get it to work ?

GR Arjen

---

