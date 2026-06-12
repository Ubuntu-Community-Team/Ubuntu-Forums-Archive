---
title: "Apt is not reinstalling my packages or reconfiguring them."
date: 2007-08-11
forum: Server Platforms
---

### Post by Gruelius on 2007-08-11
Hey all,
For some reason i buggered up my config files for apache2. Anyway hav been for the last day trying to reconfigure it and all that. but it still wont work.

Ive tried
apt-get remove *packages*
apt-get --reinstall install *packages*
apt-get -f install *packages (after removing and rm -rf *packagedir in etc*)
dpkg-reconfigure -f *packages*

One problem is that it doesnt install the apache config file again :( I might just go cold turkey untill i do my debian setup  :P

Any ideas? im probably missing something small

packages are
apache2 php5 libapache2-mod-php5 mysql-server mysql-client php5-mysql

well i just need to install the LAMP server again if thats possible. Thanks
Julius

*edit*
```
julius@tuxserver:/etc$ dir apache2
httpd.conf  mods-available
julius@tuxserver:/etc$ sudo tasksel install lamp-server
julius@tuxserver:/etc$ dir apache2/
httpd.conf  mods-available
julius@tuxserver:/etc$ sudo apt-get install apache2 php5-mysql libapache2-mod-ph                                                                                                                                p5 mysql-serve
Reading package lists... Done
Building dependency tree
Reading state information... Done
apache2 is already the newest version.
php5-mysql is already the newest version.
libapache2-mod-php5 is already the newest version.
E: Couldn't find package mysql-serve
julius@tuxserver:/etc$ sudo apt-get install apache2 php5-mysql libapache2-mod-ph                                                                                                                                p5 mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
apache2 is already the newest version.
php5-mysql is already the newest version.
libapache2-mod-php5 is already the newest version.
mysql-server is already the newest version.
The following packages were automatically installed and are no longer required:
  clamav-freshclam clamav-base libclamav2 libgmp3c2 libcurl3
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
julius@tuxserver:/etc$
```

---

### Post by ruibernardo on 2007-08-11
Hi Gruelius, 

try this:

[http://ubuntuforums.org/showpost.php?p=1751744&postcount=3](http://ubuntuforums.org/showpost.php?p=1751744&postcount=3)

---

### Post by Gruelius on 2007-08-11
no help :(

---

### Post by Gruelius on 2007-08-11
figured it out, it needs to be updated to say apache2.2-common
cheers

---

### Post by ruibernardo on 2007-08-11
Purging apache2-common and apache2 packages and installing them again should work.

It's what you want, isn't it?

---

### Post by ruibernardo on 2007-08-11
Yes, that post is a little bit outdated. Glad it helped somehow :D

---

