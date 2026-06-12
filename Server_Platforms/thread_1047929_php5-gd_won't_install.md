---
title: "php5-gd won't install"
date: 2009-01-22
forum: Server Platforms
---

### Post by skunkbad on 2009-01-22
I'm trying to install php5-gd, unfortunately, this is what I get:

```
admin@webserver:/$ sudo apt-get install php5-gd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libapache2-mod-php5 libgd2-xpm libt1-5 libxpm4 php5-common php5-mysql
Suggested packages:
  php-pear libgd-tools
The following NEW packages will be installed:
  libgd2-xpm libt1-5 libxpm4 php5-gd
The following packages will be upgraded:
  libapache2-mod-php5 php5-common php5-mysql
3 upgraded, 4 newly installed, 0 to remove and 21 not upgraded.
Need to get 2953kB/3453kB of archives.
After this operation, 1409kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err http://us.archive.ubuntu.com hardy-updates/main php5-mysql 5.2.4-2ubuntu5.2
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com hardy-updates/main libapache2-mod-php5 5.2.4-2ubuntu5.2
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com hardy-updates/main php5-common 5.2.4-2ubuntu5.2
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com hardy-updates/main php5-gd 5.2.4-2ubuntu5.2
  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/php5/php5-mysql_5.2.4-2ubuntu5.2_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.2.4-2ubuntu5.2_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.2.4-2ubuntu5.2_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/php5/php5-gd_5.2.4-2ubuntu5.2_i386.deb  404 Not Found [IP: 91.189.88.45 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

So, I see that I am getting a bunch of 404 Not Founds, and need help to get this php5-gd installed.

Thanks in advance.

---

### Post by ibutho on 2009-01-22
Have you tried running "sudo apt-get update" as suggested and then trying to install your package. If that does not work, try using a different mirror.

---

### Post by skunkbad on 2009-01-23
sudo apt-get update was the solution. Thanks!

---

