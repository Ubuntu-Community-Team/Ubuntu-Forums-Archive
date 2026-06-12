---
title: "file on NFS incorrectly reported as missing"
date: 2010-07-04
forum: Server Platforms
---

### Post by NFStroubs on 2010-07-04
I have got four webservers and one fileserver, all running Karmic and kernel 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux.

A folder on the fileserver has been exported using NFSv3 with these options: rw,async,no_subtree_check
and mounted on all four webservers with these options: defaults,rsize=32768,wsize=32768,noatime

The webservers run Apache+PHP+APC. Some php-files include other php-files from the nfs mount, and are requested by users very frequently (~ 100 times per second). Sometimes but not always if I alter an included php-file using FTP (the FTP server is ProFTPD and runs on the fileserver), the file seems missing:

user@webserver1: ~ $ ls --full-time -al /path/to/included/file.php
ls: cannot access /path/to/included/file.php: No such file or directory

I can repeat this command for hours, but the file keeps missing. Until I query the directory:

user@webserver1: ~ $ ls --full-time -al /path/to/included/ | grep file
-rwxr-xr-x  1 1002 1002 14294 2010-07-04 21:11:30.000000000 +0200 file.php

and then the first command also works.

Any suggestion would be welcome.

---

### Post by NFStroubs on 2010-07-10
*kick*

---

### Post by NFStroubs on 2010-07-24
noone?

---

