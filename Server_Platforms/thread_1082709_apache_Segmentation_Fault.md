---
title: "apache Segmentation Fault"
date: 2009-02-28
forum: Server Platforms
---

### Post by buggolo on 2009-02-28
Hi to everyone,
after a software upgrade on my "Ubuntu 8.10 Server" that included PHP and Mysql packages i have a very very great number of errors like this in my /var/log/apache2/error.log.

> 
[Sat Feb 28 11:42:04 2009] [notice] child pid 22456 exit signal Segmentation fault (11)
[Sat Feb 28 11:42:04 2009] [notice] child pid 22457 exit signal Segmentation fault (11)
[Sat Feb 28 11:42:04 2009] [notice] child pid 22458 exit signal Segmentation fault (11)
[Sat Feb 28 11:42:04 2009] [notice] child pid 22459 exit signal Segmentation fault (11)
[Sat Feb 28 11:42:04 2009] [notice] child pid 22460 exit signal Segmentation fault (11)
[Sat Feb 28 11:42:04 2009] [notice] child pid 22461 exit signal Segmentation fault (11)
[Sat Feb 28 11:42:04 2009] [notice] child pid 22462 exit signal Segmentation fault (11)
[Sat Feb 28 11:42:04 2009] [notice] child pid 22463 exit signal Segmentation fault (11)
[Sat Feb 28 11:42:04 2009] [notice] child pid 22464 exit signal Segmentation fault (11)
[Sat Feb 28 11:42:04 2009] [notice] child pid 22465 exit signal Segmentation fault (11)


Does anyone has an idea about this problem? By reading log file, it seems that this happens just after the software upgrade....

---

### Post by deadsea on 2009-03-02
I am seeing similar log messages.  I'm not sure when they started or what causes them.

---

### Post by dinoboff on 2009-03-15
I have the same problem.

After installing Apache, I got the "It works!" message when visiting [http://localhost](http://localhost).

If I install mod_wsgi (libapache2-mod-wsgi) or fast-cgi (libapache2-mod-fcgid), the page doesn't display and the error log get filled by these segment-fault error message:

[Sat Mar 14 13:58:27 2009] [notice] child pid ##### exit signal Segmentation fault (11)

I am using Ubuntu 8.04 (on a VMware Workstation 6.5.1 virtual server). I got the same problem with Debian 5 on EC2.

---

### Post by hagen00 on 2009-04-15
any ideas? i just upgraded from feisty to gutsy and then from gutsy to hardy. Now my apache is giving me segmentation faults whenever i access a page

---

### Post by de0xyrib0se on 2009-04-15
More than likely Apache is trying to load a library that isnt there after the upgrade, i would recommend reinstalling Apache.

---

### Post by rururudy on 2009-04-29
Took me a few hours to track this down, but here is what fixed if for me ... turns out the default setting of epoll=128 limits you to 128 apaches in Intrepid

> echo "fs.epoll.max_user_instances=4092" >> /etc/sysctl.conf
sysctl -p

---

