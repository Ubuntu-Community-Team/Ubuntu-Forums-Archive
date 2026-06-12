---
title: "How to install phpmyadmin without installing apache?"
date: 2006-03-17
forum: Server Platforms
---

### Post by chapterthree on 2006-03-17
**NOTE: I chose bad wording for the title of this thread.  I know phpmyadmin requires a webserver, my issue is that the phpmyadmin package requires apache (version 1) and php4, and does not seem to recognize that I have apache2 and php5 installed.**

Hey All,

I have installed apache2 and php5, but when I try to install phpmyadmin it wants to install apache and php4.  Why is this, and how can I force phpmyadmin to install without installing apache and php4?

```
root@g [/etc]# dpkg -l php5
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  php5           5.0.5-2ubuntu1 server-side, HTML-embedded scripting languag

root@g [/etc]# dpkg -l apache2
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  apache2        2.0.54-5ubuntu next generation, scalable, extendable web se
```
```
root@g [/etc]# apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
   apache-common (1.3.33-8)
   libapache-mod-php4 (4.4.0-3)
   libzzip-0-12 (0.12.83-5)
   php4-common (4.4.0-3)
   php4-mysql (4.4.0-3)
   ucf (1.18)
Suggested packages:
   apache (1.3.33-8)
   apache-ssl (1.3.33-8)
   apache-perl (1.3.33-8)
   php-pear (5.0.5-2ubuntu1.2)
   php4-gd (4.4.0-3)
   php5-gd (5.0.5-2ubuntu1.2)
Recommended packages:
   php4-mcrypt (4.3.10-1ubuntu1)
   php5-mcrypt ()
The following NEW packages will be installed:
   apache-common (1.3.33-8)
   libapache-mod-php4 (4.4.0-3)
   libzzip-0-12 (0.12.83-5)
   php4-common (4.4.0-3)
   php4-mysql (4.4.0-3)
   phpmyadmin (2.6.4-pl1-1ubuntu1)
   ucf (1.18)
0 upgraded, 7 newly installed, 0 to remove and 2 not upgraded.
Need to get 5557kB of archives.
After unpacking 18.2MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

---

### Post by TTT_travis on 2006-03-18
hmm that is very odd. What you can do is goto the [phpymyadmin]("http://www.phpmyadmin.net/home_page/") site and download it from there and install it I don't remember it being too difficult to install last time I did it manually. or if you don't want to try that you could get the deb and extract it manually using ar -x package.deb and extract the data.tgz inside that and move everything to the proper places.

---

### Post by chapterthree on 2006-03-18
Yeah I've thought about going that route, and it looks like I may have to.  It's just annoying because I'll have to manual updating, rather than letting apt take care of the updates :(

---

### Post by Zeroangel on 2006-03-18
phpMyAdmin is a web front end. In other words you need to be running a server like apache in order to even access it.

Manual updating isn't difficult at all. All you would need to do is extract the phpMyAdmin folder into your www folder and access it through localhost/phpMyAdmin (or wherever you have it installed).

Anyways, there is a GTK frontend  (not just a web frontend) called mysql-admin that will let you do some things with your database. Its in the repos, you should check it out.

---

### Post by chapterthree on 2006-03-18
[QUOTE=Zeroangel]hmm, doesn't phpMyAdmin require a web server to run? The last time I checked, I had to access it through localhost/phpmyadmin while apache was running.

Anyways, there is a GTK frontend (not just a web frontend) that will let you do some things with your database. It's called mysql-admin , it should be in the repos.[/QUOTE]
This is on a headless server.

Also please read carefully: "I have installed apache2 and php5..." (translation, I do have a webserver, but apparently not a webserver that phpmyadmin wants to use hehe)

---

### Post by gmclachl on 2006-03-18
phpMyAdmin runs fine on apache2.

 I would report it as a defect to the package maintainer. There is no reason to restrict it to apache alone.

 George

---

### Post by Koybe on 2006-03-18
Maybe this is because your're missing libapache2-mod-php5 package?

---

### Post by majikstreet on 2006-03-18
you have to have some sort of webserver for it to work.. you can download phpmyadmin from the web and untar it or whatever, but you still need a webserver - if you don't want to use apache there are other ones such as monkey or cherokee

---

### Post by Velvet Elvis on 2006-03-18
Here's a howto for how to have php4 and php5 coexisting on a debian or ubuntu system:

[http://www.howtoforge.com/apache2_with_php5_and_php4](http://www.howtoforge.com/apache2_with_php5_and_php4)

I have a hunch that php4 is trying to install libapache-mod-php4 and that's what's trying to drag apache into it.  Once you have libapache2-mod-php4 on there it should be complacent with you having apache2.

It seems like there should be a less complicated solution.

---

### Post by LordHunter317 on 2006-03-19
Post 'apt-cache show phpmyadmin'

---

### Post by chapterthree on 2006-03-19
[QUOTE=Koybe]Maybe this is because your're missing libapache2-mod-php5 package?[/QUOTE]
No, this package is installed:
```
root@www [~]# dpkg -l libapache2-mod-php5
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name             Version          Description
+++-================-================-================================================
ii  libapache2-mod-p 5.0.5-2ubuntu1.2 server-side, HTML-embedded scripting language (a
```

[QUOTE=LordHunter317]Post 'apt-cache show phpmyadmin'[/QUOTE]
```
root@www [~]# apt-cache show phpmyadmin
Package: phpmyadmin
Priority: extra
Section: universe/web
Installed-Size: 10856
Maintainer: Piotr Roszatycki <dexter@debian.org>
Architecture: all
Version: 4:2.6.4-pl1-1ubuntu1
Depends: php4 | php4-cgi | php5 | php5-cgi, php4-mysql | php5-mysql | php5-mysqli, apache2 | httpd, debconf (>= 0.2.26), ucf (>= 0.8)
Recommends: php4-mcrypt | php5-mcrypt
Suggests: mysql-server (>= 3.23.36), php4-gd | php5-gd
Filename: pool/universe/p/phpmyadmin/phpmyadmin_2.6.4-pl1-1ubuntu1_all.deb
Size: 2902948
MD5sum: c1dd92145bbed0c8502be8e8d6898743
Description: set of PHP-scripts to administrate MySQL over the WWW
 phpMyAdmin is intended to handle the administration of MySQL over the WWW.
 Currently it can:
  - create and drop databases
  - create, copy, drop and alter tables
  - delete, edit and add fields
  - execute any SQL-statement, even batch-queries
  - manage keys on fields
  - load text files into tables
  - create and read dumps of tables
  - export and import CSV data
  - administer one single database as well as a whole database server
  - communicate in 50 different languages
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```

---

