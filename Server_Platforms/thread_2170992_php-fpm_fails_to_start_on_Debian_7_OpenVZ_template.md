---
title: "php-fpm fails to start on Debian 7 OpenVZ template"
date: 2013-08-28
forum: Server Platforms
---

### Post by CharlesA on 2013-08-28
Hey,

I know this should probably go in Other/OS, but it is a server question. :p

I'm trying to set up a VPS with Nginx and php5-fpm but for whatever reason it bombs out when trying to start php5-fpm:

```
root@serenity:~# apt-get install nginx php5-fpm
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libgd2-noxpm libjpeg8 libonig2 libossp-uuid16 libqdbm14 libxslt1.1 nginx-common nginx-full php5-common
Suggested packages:
  libgd-tools uuid nginx-doc fcgiwrap php-pear
The following NEW packages will be installed:
  libgd2-noxpm libjpeg8 libonig2 libossp-uuid16 libqdbm14 libxslt1.1 nginx nginx-common nginx-full php5-common php5-fpm
0 upgraded, 11 newly installed, 0 to remove and 9 not upgraded.
Need to get 5141 kB of archives.
After this operation, 13.8 MB of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 http://packages.dotdeb.org/ wheezy-php55/all php5-common i386 5.5.1-1~dotdeb.1 [680 kB]
Get:2 http://ftp.debian.org/debian/ wheezy/main libjpeg8 i386 8d-1 [132 kB]
Get:3 http://ftp.debian.org/debian/ wheezy/main libgd2-noxpm i386 2.0.36~rc1~dfsg-6.1 [229 kB]
Get:4 http://packages.dotdeb.org/ wheezy-php55/all php5-fpm i386 5.5.1-1~dotdeb.1 [2854 kB]
Get:5 http://ftp.debian.org/debian/ wheezy/main libxslt1.1 i386 1.1.26-14.1 [251 kB]
Get:6 http://ftp.debian.org/debian/ wheezy/main libonig2 i386 5.9.1-1 [134 kB]
Get:7 http://packages.dotdeb.org/ wheezy/all nginx-common all 1.4.2-1~dotdeb.1 [78.3 kB]
Get:8 http://ftp.debian.org/debian/ wheezy/main libqdbm14 i386 1.8.78-2 [151 kB]
Get:9 http://packages.dotdeb.org/ wheezy/all nginx-full i386 1.4.2-1~dotdeb.1 [505 kB]
Get:10 http://packages.dotdeb.org/ wheezy/all nginx all 1.4.2-1~dotdeb.1 [65.8 kB]
Get:11 http://ftp.debian.org/debian/ wheezy/main libossp-uuid16 i386 1.6.2-1.3 [59.6 kB]
Fetched 5141 kB in 13s (371 kB/s)
Selecting previously unselected package libjpeg8:i386.
(Reading database ... 20754 files and directories currently installed.)
Unpacking libjpeg8:i386 (from .../libjpeg8_8d-1_i386.deb) ...
Selecting previously unselected package libgd2-noxpm:i386.
Unpacking libgd2-noxpm:i386 (from .../libgd2-noxpm_2.0.36~rc1~dfsg-6.1_i386.deb) ...
Selecting previously unselected package libxslt1.1:i386.
Unpacking libxslt1.1:i386 (from .../libxslt1.1_1.1.26-14.1_i386.deb) ...
Selecting previously unselected package php5-common.
Unpacking php5-common (from .../php5-common_5.5.1-1~dotdeb.1_i386.deb) ...
Selecting previously unselected package libonig2.
Unpacking libonig2 (from .../libonig2_5.9.1-1_i386.deb) ...
Selecting previously unselected package libqdbm14.
Unpacking libqdbm14 (from .../libqdbm14_1.8.78-2_i386.deb) ...
Selecting previously unselected package php5-fpm.
Unpacking php5-fpm (from .../php5-fpm_5.5.1-1~dotdeb.1_i386.deb) ...
Selecting previously unselected package libossp-uuid16.
Unpacking libossp-uuid16 (from .../libossp-uuid16_1.6.2-1.3_i386.deb) ...
Selecting previously unselected package nginx-common.
Unpacking nginx-common (from .../nginx-common_1.4.2-1~dotdeb.1_all.deb) ...
Selecting previously unselected package nginx-full.
Unpacking nginx-full (from .../nginx-full_1.4.2-1~dotdeb.1_i386.deb) ...
Selecting previously unselected package nginx.
Unpacking nginx (from .../nginx_1.4.2-1~dotdeb.1_all.deb) ...
Processing triggers for man-db ...
Setting up libjpeg8:i386 (8d-1) ...
Setting up libgd2-noxpm:i386 (2.0.36~rc1~dfsg-6.1) ...
Setting up libxslt1.1:i386 (1.1.26-14.1) ...
Setting up php5-common (5.5.1-1~dotdeb.1) ...

Creating config file /etc/php5/mods-available/pdo.ini with new version

Creating config file /etc/php5/mods-available/opcache.ini with new version
Setting up libonig2 (5.9.1-1) ...
Setting up libqdbm14 (1.8.78-2) ...
Setting up php5-fpm (5.5.1-1~dotdeb.1) ...

Creating config file /etc/php5/fpm/php.ini with new version
[COLOR="#FF0000"]start: Job failed to start
invoke-rc.d: initscript php5-fpm, action "start" failed.
dpkg: error processing php5-fpm (--configure):
 subprocess installed post-installation script returned error exit status 1[/COLOR]
Setting up libossp-uuid16 (1.6.2-1.3) ...
Setting up nginx-common (1.4.2-1~dotdeb.1) ...
Setting up nginx-full (1.4.2-1~dotdeb.1) ...
Setting up nginx (1.4.2-1~dotdeb.1) ...
[COLOR="#FF0000"]Errors were encountered while processing:
 php5-fpm
E: Sub-process /usr/bin/dpkg returned an error code (1)

```[/COLOR]

I'm using the OpenVZ template from OpenVZ.org and this occurs on both my test VPS (at home running on Proxmox) and on my hosted VPS. I do have another VPS that was running a minimal install of Debian 7 and that installed fine.

Now my question is this: Is there a way to see why php5-fpm is failing to start?

I read [here]("http://stackoverflow.com/questions/15419540/php-fpm-5-4-cannot-start-just-get-a-failed-message") to try starting php5-fpm with the -n switch and that apparently succeeded.

```
root@serenity:~# /usr/sbin/php5-fpm -n
root@serenity:~# /usr/sbin/php5-fpm -n
[28-Aug-2013 15:31:15] ERROR: An another FPM instance seems to already listen on /var/run/php5-fpm.sock
[28-Aug-2013 15:31:15] ERROR: FPM initialization failed
```

Is there any way to figure out what is causing php5-fpm to fail to start on a clean install?

Thanks.

---

### Post by CharlesA on 2013-08-28
It looks like this is due to the "official" Debian 7 OpenVZ template uses upstart instead of sysvinit.

If I replace upstart, php5-fpm starts but now I can't reboot the machine...

EDIT: Fixed the problem by installing PHP 5.4.19 instead of PHP 5.5.1.1.

The issue occurred because of the upstart script wasn't working correctly.
[https://github.com/gplessis/dotdeb-php5/pull/41](https://github.com/gplessis/dotdeb-php5/pull/41)

---

### Post by zieru on 2013-09-26
hii, It's easy you don't need to downgrade php, you can always use upstart by holding it from upgrade
I don't know about ubuntu
but maybe it's same like debian
for debian first install wajig
apt-get install wajig
wajig hold upstart

---

