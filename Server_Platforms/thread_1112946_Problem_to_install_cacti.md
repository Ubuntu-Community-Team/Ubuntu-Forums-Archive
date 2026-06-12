---
title: "Problem to install cacti"
date: 2009-04-01
forum: Server Platforms
---

### Post by rado3105 on 2009-04-01
Hi I installed rrdtool, php5, mysql, apache2 and the last cacti using:
> r-c@rclr-srv:~$ sudo apt-get install cacti
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  cacti
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
Need to get 0B/1837kB of archives.
After this operation, 5186kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package cacti.
(Reading database ... 23835 files and directories currently installed.)
Unpacking cacti (from .../cacti_0.8.7b-2ubuntu1_all.deb) ...
Setting up cacti (0.8.7b-2ubuntu1) ...
dbconfig-common: writing config to /etc/dbconfig-common/cacti.conf
Replacing config file /etc/cacti/debian.php with new version
 * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.76.4 for ServerName

It ends with that, seems that everything is fine, but I cant login to cacti, writing this to browser: [http://192.168.76.4/cacti/](http://192.168.76.4/cacti/) shows blank page can you help or how to continue to set cacti?

I have installed ubuntu 8.04 server edition.

---

