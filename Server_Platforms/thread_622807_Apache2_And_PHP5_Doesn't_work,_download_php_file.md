---
title: "Apache2 And PHP5 Doesn't work, download php file"
date: 2007-11-25
forum: Server Platforms
---

### Post by arjenlodder on 2007-11-25
Hello, 
I've installed Apache2 and Mysql (server/client) and PHP5 (everything).
I've installed HLstatsX for Counter Strike Source, this uses PHP, 
When I've it, yesterday, everything worked but now when i restarted my computer he can't find the PHP files. Instead, he tries to download it.
I've searched the whole forums, found sulutions, tried them... but, nothing seems to work, I even REinstalled everything, and my FireFox cache has noting to do with it, cleant it multiple times, and in Internet Explorer on windows, i got exactly the same thing.
Do you know how to solve the problem ?
My site: [http://arjen.myftp.org](http://arjen.myftp.org)
I doe have got a test.html and that works. but index.php not.

GR Arjen

---

### Post by qsr.nrwn on 2007-11-25
Same problem...

I just added this following lines to httpd.conf

```

AddType application/x-httpd-php .php3 .php
AddType application/x-httpd-php-source .phps

```

It seems to work fine... described in Beginning PHP, Apache, MySQL® Web Development (Michael Glass, Yann Le Scouarnec, Elizabeth Naramore, Gary Mailer, Jeremy Stolz, and Jason Gerner), by Wiley and Sons

By the way I need some help about configuring mysql

---

### Post by arjenlodder on 2007-11-25
Hey, 
thanks for your reaction, but it still doesn't work.
It still asks me to download the PHP, but when i start apache it gives NO error.

GR Arjen

---

### Post by qsr.nrwn on 2007-11-25
Have you restarted apache2 daemon?

---

### Post by qsr.nrwn on 2007-11-25
I followed the documentation on [PHP5 - Scripting Language]("https://help.ubuntu.com/7.10/server/C/php5.html")

As a quick start guide you should run the next commands

```
sudo apt-get install php5-common php5 libapache2-mod-php5
sudo apt-get install php5-cli
sudo apt-get install php5-cgi
sudo apt-get install php5-mysql
```
Later you should run this command and select php5
```
a2enmod 
```

And finally restart the apache2 daemon via
```
sudo /etc/init.d/apache2 restart 
```

---

### Post by arjenlodder on 2007-11-26
Hey, 
Thanx for saying this.
I have done everything you said, in that order.
Found out that 3 packages weren't installed, installed them and restarted everything.

But it doesn't work :(
Any other ideas ?

GR Arjen

---

### Post by zdux0012 on 2007-12-06
I didn't believe you when you reported this problem, but I have the same problem.
I think it would have been avoided if php were installed before apache, but not sure. 
I'll keep this forum updated with my progress

---

### Post by zdux0012 on 2007-12-06
Not a working solution for me but a logical move in the right direction:

Add 
AddHandler application/x-httpd-php .php

to /etc/apache2/mods-enabled/mime.conf

I'm surprised this was not already set, this might be the clue someone needs to tell us what didn't happen in the configuration of php

---

### Post by zdux0012 on 2007-12-06
Be sure to clear your browser's cache before testing your site again.
install  libapache2-mod-auth-mysql php5-mysql

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by zdux0012 on 2007-12-06
These combinations I've posted made it work for me.

---

### Post by F@Ze on 2008-07-16
Old topic, but I found having the same problem. I think the 'official' way is not to alter mime.conf or any other conf file in that folder. Apache just loads every conf file in that folder.
There is an mods-available folder. The name speaks for itself.
In that folder there is a php5.conf and php5.load. You need both that modules.
now go to the mods-enabled folder.
Enter: ln -s ../php5.conf
ln -s ../php5.load

now restart apache:
/etc/init.d/apache2 restart
and php should work ;)

---

### Post by bodhi.zazen on 2008-09-13
I know this is a closed section of the forums, but this page come up when I ran into the same problem.

The solutions on this page did not help, but this page did :

[http://www.ubuntugeek.com/apache2-web-server-installation-with-php4-and-php5-support-in-ubuntu.html](http://www.ubuntugeek.com/apache2-web-server-installation-with-php4-and-php5-support-in-ubuntu.html)


> For php5 support

 sudo apt-get install libapache2-mod-php5 php5-cli php5-common php5-cgi
 
Next we edit /etc/apache2/apache2.conf file and check the index files are correct
 
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml

Then re-start apache and clear your cache.

---

