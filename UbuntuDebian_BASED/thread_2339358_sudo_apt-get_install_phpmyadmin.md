---
title: "sudo apt-get install phpmyadmin"
date: 2016-10-07
forum: Ubuntu/Debian BASED
---

### Post by kumar1432 on 2016-10-07
Reading package lists... Done
Building dependency tree       
Reading state information... Done
phpmyadmin is already the newest version (4:4.5.4.1-2ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up dbconfig-common (2.0.4ubuntu1) ...
dpkg: error processing package dbconfig-common (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    dpkg: dependency problems prevent configuration of dbconfig-mysql:
 dbconfig-mysql depends on dbconfig-common (= 2.0.4ubuntu1); however:
  Package dbconfig-common is not configured yet.


dpkg: error processing package dbconfig-mysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpmyadmin:
 phpmyadmin depends on dbconfig-mysql | dbconfig-no-thanks | dbconfig-common (<< 2.0.0); however:
  Package dbconfig-mysql is not configured yet.
  Package dbconfig-no-thanks is not installed.
  Version of dbconfig-common on system is 2.0.4ubuntu1.


dpkg: error processing package phpmyadmin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dbconfig-common
 dbconfig-mysql
 phpmyadmin
^[[AE: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by QIII on 2016-10-07
Duplicate of [https://ubuntuforums.org/showthread.php?t=2339356](https://ubuntuforums.org/showthread.php?t=2339356).

Please do not create duplicate threads.  This is the second duplicate the staff has had to deal with.

Closed.

---

