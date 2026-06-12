---
title: "apache php problem"
date: 2007-02-10
forum: Server Platforms
---

### Post by matt91 on 2007-02-10
today removed a package which also removed apache aswell. so i reinstalled apache2, it started but wasnt loading php with it, just giving out php sources. so i then decided to remove apache2 and php5 aswell as all the associated apache2 and php5 packages to go with them. reinstalled them all (with the libapache2-mod-php5) and it was the same. so then i decided to remove them all again and delete /etc/apache2 directory. when i went to reinstall all the packages again i got:
> root@server:~# apt-get install php5 php5-mysql libapache2-mod-php5 apache2 apache2-common apache2-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apache2-mpm-prefork libapr0 libpcre3 php5-common php5-mysqli
Suggested packages:
  apache2-doc php-pear
The following NEW packages will be installed
  apache2 apache2-common apache2-mpm-prefork apache2-utils libapache2-mod-php5 libapr0 libpcre3 php5 php5-common php5-mysql php5-mysqli
0 upgraded, 11 newly installed, 0 to remove and 3 not upgraded.
Need to get 3974kB of archives.
After unpacking 10.6MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main libapr0 2.0.55-4ubuntu4 [137kB]
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main php5-common 5.1.6-1ubuntu2.1 [139kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main libpcre3 6.4-2ubuntu1 [174kB]
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libapache2-mod-php5 5.1.6-1ubuntu2.1 [2318kB]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main apache2-utils 2.0.55-4ubuntu4 [93.1kB]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main apache2-common 2.0.55-4ubuntu4 [807kB]
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main apache2-mpm-prefork 2.0.55-4ubuntu4 [206kB]
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main apache2 2.0.55-4ubuntu4 [36.0kB]        
Get: 9 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main php5 5.1.6-1ubuntu2.1 [1070B]                                                                                              
Get: 10 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main php5-mysqli 5.1.6-1ubuntu2.1 [39.5kB]                                                                                     
Get: 11 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main php5-mysql 5.1.6-1ubuntu2.1 [23.1kB]                                                                                      
Fetched 3974kB in 11s (332kB/s)                                                                                                                                                 
Preconfiguring packages ...
Selecting previously deselected package libapr0.
(Reading database ... 25607 files and directories currently installed.)
Unpacking libapr0 (from .../libapr0_2.0.55-4ubuntu4_i386.deb) ...
Selecting previously deselected package libpcre3.
Unpacking libpcre3 (from .../libpcre3_6.4-2ubuntu1_i386.deb) ...
Selecting previously deselected package apache2-utils.
Unpacking apache2-utils (from .../apache2-utils_2.0.55-4ubuntu4_i386.deb) ...
Selecting previously deselected package apache2-common.
Unpacking apache2-common (from .../apache2-common_2.0.55-4ubuntu4_i386.deb) ...
Selecting previously deselected package apache2-mpm-prefork.
Unpacking apache2-mpm-prefork (from .../apache2-mpm-prefork_2.0.55-4ubuntu4_i386.deb) ...
Selecting previously deselected package apache2.
Unpacking apache2 (from .../apache2_2.0.55-4ubuntu4_i386.deb) ...
Selecting previously deselected package php5-common.
Unpacking php5-common (from .../php5-common_5.1.6-1ubuntu2.1_i386.deb) ...
Selecting previously deselected package libapache2-mod-php5.
Unpacking libapache2-mod-php5 (from .../libapache2-mod-php5_5.1.6-1ubuntu2.1_i386.deb) ...
Selecting previously deselected package php5.
Unpacking php5 (from .../php5_5.1.6-1ubuntu2.1_all.deb) ...
Selecting previously deselected package php5-mysqli.
Unpacking php5-mysqli (from .../php5-mysqli_5.1.6-1ubuntu2.1_i386.deb) ...
Selecting previously deselected package php5-mysql.
Unpacking php5-mysql (from .../php5-mysql_5.1.6-1ubuntu2.1_i386.deb) ...
Setting up libapr0 (2.0.55-4ubuntu4) ...

Setting up libpcre3 (6.4-2ubuntu1) ...

Setting up apache2-utils (2.0.55-4ubuntu4) ...
Setting up apache2-common (2.0.55-4ubuntu4) ...

Setting up apache2-mpm-prefork (2.0.55-4ubuntu4) ...
It looks like you've deleted /etc/apache2/mods-available/cgi.load, so cgi can not be enabled.  To fix this, please purge and reinstall apache2-common.
 * Starting apache 2.0 web server...                                                                                                                                             apache2: could not open document config file /etc/apache2/apache2.conf
                                                                                                                                                                          [fail]
invoke-rc.d: initscript apache2, action "start" failed.

Setting up apache2 (2.0.55-4ubuntu4) ...
Setting up php5-common (5.1.6-1ubuntu2.1) ...
Setting up libapache2-mod-php5 (5.1.6-1ubuntu2.1) ...

Setting up php5 (5.1.6-1ubuntu2.1) ...
Setting up php5-mysql (5.1.6-1ubuntu2.1) ...

Setting up php5-mysqli (5.1.6-1ubuntu2.1) ...

root@server:~# 

and when i try to start  with ini.d i get:
> root@server:~# /etc/init.d/apache2 start
 * Starting apache 2.0 web server...                                                                                                                                             apache2: could not open document config file /etc/apache2/apache2.conf
                                                                                                                                                                          [fail]
root@server:~# 


my thinking is that apache should create the apache2.conf its self? what am i doing wrong here?

---

### Post by matt91 on 2007-02-10
anybody? any example apache2.conf coz it dont look like its going to make its own one:(

---

### Post by matt91 on 2007-02-10
how can i uninstall every php and apache including the configs and start from scratch (without reinstalling ubuntu) becouse apt-get doesnt seem to do this and expects the configs there before they are actually installed.:confused: :mad: :(

---

### Post by matt91 on 2007-02-10
anybody???

---

### Post by matt91 on 2007-02-10
please:confused:

---

### Post by localzuk on 2007-02-10
> **matt91 said:**
> today removed a package which also removed apache aswell. so i reinstalled apache2, it started but wasnt loading php with it, just giving out php sources. so i then decided to remove apache2 and php5 aswell as all the associated apache2 and php5 packages to go with them. reinstalled them all (with the libapache2-mod-php5) and it was the same. so then i decided to remove them all again and delete /etc/apache2 directory. when i went to reinstall all the packages again i got:


and when i try to start  with ini.d i get:


my thinking is that apache should create the apache2.conf its self? what am i doing wrong here?


Do an apt-get --purge remove apache2-common, then re-install apache2.

This should recreate the config files AFAIK.

---

### Post by matt91 on 2007-02-10
thank you very much, its now all working:D

---

