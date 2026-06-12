---
title: "php not working"
date: 2008-12-26
forum: Server Platforms
---

### Post by jnw222 on 2008-12-26
i installed the "lamp server" task in tasksel on ubuntu-jaunty (up to date) but now when i try to go to install phpbb, opening firefox to the index.php in [http://localhost/phpbb3](http://localhost/phpbb3) opens a download dialog

html works fine 
mysql works fine 


how do i set up php so that the scripts run like html pages in a browser (aka standard setup)

---

### Post by mbeach on 2008-12-26
this is becoming quite a common question.

Perhaps this link will help:
[http://ubuntuforums.org/showpost.php?p=5780073&postcount=12](http://ubuntuforums.org/showpost.php?p=5780073&postcount=12)

---

### Post by jnw222 on 2008-12-26
not working

all php scripts just start a download

---

### Post by mbeach on 2008-12-26
can you post the results of:
sudo apt-get install libapache2-mod-php5

then restart apache
sudo /etc/init.d/apache2 restart

---

### Post by jnw222 on 2008-12-26
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libapache2-mod-php5 is already the newest version.
The following packages were automatically installed and are no longer required:
  mobile-broadband-provider-info bc libgnome-desktop-2-7 python-gtkhtml2
  python-imaging libsdl-ttf2.0-0 python-sexy libgtkhtml2-0
  python-launchpad-integration libneon26-gnutls poppler-utils foomatic-db
  libopenobex1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


 * Restarting web server apache2      [ OK ]

---

### Post by jnw222 on 2008-12-26
do you need my apache2 configuration files?

---

### Post by Dr Small on 2008-12-26
Did you install php5?

---

### Post by jnw222 on 2008-12-27
Building dependency tree       
Reading state information... Done
php5 is already the newest version.

so yes

---

### Post by jnw222 on 2008-12-27
got it working

reinstall all related packages and install some others

---

### Post by mbeach on 2008-12-30
out of curiosity what were the others.  Listing them here may assist the next person to run into this problem.

---

### Post by big-t on 2008-12-31
well i did follow this guide and everything is working, this is for 
apache2, php , mysql and phpmyadmin.

tips: use gedit insted of vi when you are gonna edit the config files.

[http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100](http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100)

good luck :D

---

