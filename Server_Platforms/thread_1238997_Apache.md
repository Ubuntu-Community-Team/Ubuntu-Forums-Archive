---
title: "Apache"
date: 2009-08-13
forum: Server Platforms
---

### Post by Pakia on 2009-08-13
I run an Ubuntu server with Apache2, Bind9, Postfix, MYSQL and Squid. My OS runs of sda which is encrypted. My db and web pages are in media/sdc1 a totally seperate HD. I have a further HD sdb1 which I use for backup and my swap is a usb allocated as sdd1. I administer with webmin. Recently my sda HD gave up the ghost and I was forced to install a new one. I installed Ubuntu server 9.10 onto the new HD. I have give my user account read write permission on media/sdc1/ so that Apache can access the web pages. All seems to be Ok and my web pages (7 running as virtual hosts) are listed in the Apache2 sites enabled folder.

The problem is when I connect to my server only the var/www is being shown on the internet? There seems to be something missing between my var/www and Apache2 sites-enabled connection?

My test web site is [http://www.alt-it.tk](http://www.alt-it.tk)

I am sure it is only something minor that I have forgotten.

Any help and comments would be highly appreciated

Thanks in advance

---

### Post by Pakia on 2009-08-14
Fixed. Made a sym link between sdc1 and var/www and chmod and chown with permission 775

---

