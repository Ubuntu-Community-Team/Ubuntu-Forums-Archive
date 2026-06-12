---
title: "apache2 won't start"
date: 2006-08-21
forum: Server Platforms
---

### Post by macwunder on 2006-08-21
Yet another apache2 won't start plea...

It was working a couple days ago, but now it doesn't. The error when trying to start:

admin@qzoneinc:~$ sudo /etc/init.d/apache2 start
 * Starting apache 2.0 web server...
/usr/sbin/apache2ctl: line 78:  6680 Illegal instruction     $HTTPD -k start -DSSL
   ...fail!

error.log has nothing of value...

admin@qzoneinc:/var/log/apache2$ cat error.log
[Sun Aug 20 06:25:08 2006] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 configured -- resuming normal operations
[Sun Aug 20 08:48:49 2006] [notice] caught SIGTERM, shutting down

I've tried removing apache2 and re-installing, no difference. I've tried dpkg-reconfigure apache2-common, no difference.

Help a ubuntu newbie/YDL convert brotha out. Thanks!

---

### Post by Cope57 on 2006-08-22
Try this, from root type:

mv /etc/httpd/conf/httpd.conf.bak /etc/httpd/conf/httpd.conf

if asked to overwrite, type Y and [enter].


Or next time you can just try

vi /etc/httpd/conf/httpd.conf
:182

take a look at what is causing the problem and then if you can't fix use your backups.

---

### Post by macwunder on 2006-08-22
I suppose I should have stated that I'm on Ubuntu 6.06-1 server...

Apache2's confs live in /etc/apache2, but that file hasn't been modified:

[FONT="Courier New"]admin@qzoneinc:/etc/apache2$ ls -la
total 80
drwxr-xr-x  8 root root  4096 2006-08-11 17:54 .
drwxr-xr-x 64 root root  4096 2006-08-21 22:13 ..
-rw-r--r--  1 root root 12482 2006-05-28 20:55 apache2.conf
drwxr-xr-x  2 root root  4096 2006-08-13 12:43 conf.d
-rw-r--r--  1 root root   748 2006-05-28 20:43 envvars
-rw-r--r--  1 root root   268 1956-08-29 22:27 httpd.conf
-rw-r--r--  1 root root 12441 2006-05-28 20:55 magic
drwxr-xr-x  2 root root  4096 2006-08-11 17:54 mods-available
drwxr-xr-x  2 root root  4096 1956-08-29 22:27 mods-enabled
-rw-r--r--  1 root root    10 1956-08-29 22:27 ports.conf
-rw-r--r--  1 root root  2266 2006-05-28 20:55 README
drwxr-xr-x  2 root root  4096 2006-08-11 17:54 sites-available
drwxr-xr-x  2 root root  4096 1956-08-29 22:27 sites-enabled
drwxr-xr-x  2 root root  4096 2006-05-28 20:55 ssl[/FONT]

Thanks anyway... Anyone else?

---

### Post by macwunder on 2006-08-23
> **macwunder said:**
> Thanks anyway... Anyone else?

No one else seen this or have any ideas? :confused:

---

### Post by harisund on 2006-08-23
Did you try the clean-everything-and-start-as-if-nothing-happened method? 

sudo apt-get --purge remove apache2 apache2-common php5 libapache2-mod-php5
sudo apt-get install (everything above again)

---

### Post by macwunder on 2006-08-23
I had tried to --purge apache2, but giving your suggestion a go I see that the apache2-common is where the configs are expunged.

](*,) 

Many thanks! I'm good now.

---

