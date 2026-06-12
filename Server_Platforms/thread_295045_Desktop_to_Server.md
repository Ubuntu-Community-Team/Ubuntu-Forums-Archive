---
title: "Desktop to Server?"
date: 2006-11-07
forum: Server Platforms
---

### Post by mateo107 on 2006-11-07
I just installed Ubuntu Desktop 6.10 as I want a "user interface" on my server...

Is there an "easy" install to convert this PC into an HTTP server.  I just want it running MySQL, PHP, and HTTP(s)...  Also, do any pre-packaged deals come configured with PHPMySqlAdmin?

Thanks a bunch!

-matt-

---

### Post by Klaidas on 2006-11-07
So did you install a desktop and want a server...
Or did you install a server and want some graphics? 

If it's #1, then [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
If it's #2, sudo aptitude install ubuntu-desktop

---

### Post by NewbieNik on 2006-11-08
> **mateo107 said:**
> I just installed Ubuntu Desktop 6.10 as I want a "user interface" on my server...

Is there an "easy" install to convert this PC into an HTTP server.  I just want it running MySQL, PHP, and HTTP(s)...  Also, do any pre-packaged deals come configured with PHPMySqlAdmin?

Thanks a bunch!

-matt-

Simple answer is yes. Go to your terminal and enter:-

sudo apt-get install apache2 php5 mysql-server php5-mysql phpmyadmin

This will install all your package needs. Then you just need to activate PHP processing in APache2 by amending the conf file.

Sudo gedit /etc/apache2/apache2.conf

and change the two lines

#AddType application/x-httpd-php .php
#AddType application/x-httpd-php-source .phps

to

AddType application/x-httpd-php .php .phtml .html
AddType application/x-httpd-php-source .phps

et voila, http yourself to smiley destruction!!!

---

### Post by lazyart on 2006-11-08
I found it easier to install a LAMP Server from the Server CD, then from the command line 

sudo apt-get install xubuntu-desktop
sudo startxfce

Once the gui was up I installed webmin.  Don't need the gui anymore because you can administer from another machine via [https://server:10000](https://server:10000)

GUI eats up CPU time, which you'd rather dedicate to serving pages.  I was shocked to see that webmin can also install other packages for you, such as a mailserver, ldap.  Really, you can do everything from webmin.

---

### Post by mateo107 on 2006-11-08
OK....

I changed my installation and I've installed the SERVER version but I want a graphic interface too... just for the time being, since it's what I'm comfortable with.

I've tried: 
> sudo apt-get install xubuntu-desktop
but i get an error:
> E: Couldn't find package xubuntu-desktop and then it bails me back to a command line

also... is it true that there is no ROOT password.  I tried "start xfrce" but it says I need root... but i never got asked to set a root password.

Thanks again everyone!

---

### Post by lazyart on 2006-11-08
Root is disabled in Ubuntu.  The command is actually startxfce (I made a typo originally) and that wouldn't need root... but you have to get a desktop first.

I had problems reaching the repositories when installing server.  For some reason I couldn't get "out" unless I manually configured my network.

If you have the desktop CD, I suppose you could put it in, then

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop

---

### Post by mateo107 on 2006-11-09
I've gotten XUbuntu to install... but how do I change the boot options to allow me to either log into the shell (err, is that the right terminolgy) OR the GUI.  I want the option to do either, with the default being the GUI.

---

