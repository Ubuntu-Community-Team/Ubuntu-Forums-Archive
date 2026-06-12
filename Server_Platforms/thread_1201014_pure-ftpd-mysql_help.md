---
title: "pure-ftpd-mysql help"
date: 2009-06-30
forum: Server Platforms
---

### Post by crzyone9584 on 2009-06-30
I get this error after installing pur-ftpd-mysql

Its on a vps with ubuntu 8.10 intrepid

> apt-get install pure-ftpd-mysql
Reading package lists... Done
Building dependency tree
Reading state information... Done
pure-ftpd-mysql is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up pure-ftpd-mysql (1.0.21-11.2ubuntu1) ...
Starting ftp server: Running: /usr/sbin/pure-ftpd-mysql-virtualchroot -l mysql:/etc/pure-ftpd/db/mysql.conf -l pam -O clf:/var/log/pure-ftpd/transfer.log -E -u 1000 -B
invoke-rc.d: initscript pure-ftpd-mysql, action "start" failed.
dpkg: error processing pure-ftpd-mysql (--configure):
subprocess post-installation script returned error exit status 252
Errors were encountered while processing:
pure-ftpd-mysql 

Is there a way to fix that?

im following this tutorial on to set it up.

[http://www.howtoforge.com/perfect-server-ubuntu-8.10-ispconfig-3-p4](http://www.howtoforge.com/perfect-server-ubuntu-8.10-ispconfig-3-p4)

Step 15

---

