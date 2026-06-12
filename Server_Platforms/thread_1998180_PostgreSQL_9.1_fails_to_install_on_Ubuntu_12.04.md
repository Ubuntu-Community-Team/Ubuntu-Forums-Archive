---
title: "PostgreSQL 9.1 fails to install on Ubuntu 12.04"
date: 2012-06-06
forum: Server Platforms
---

### Post by hendrel on 2012-06-06
When I try to install PostgreSQL 9.1 using ```
sudo apt-get install postgresql-9.1
``` I get the following error message:

> 
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  oidentd ident-server locales-all
The following NEW packages will be installed:
  postgresql-9.1
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0 B/4Â*302 kB of archives.
After this operation, 11,5 MB of additional disk space will be used.
Selecting previously unselected package postgresql-9.1.
(Reading database ... 44969 files and directories currently installed.)
Unpacking postgresql-9.1 (from .../postgresql-9.1_9.1.4-0ubuntu12.04_i386.deb) ...
Setting up bind9 (1:9.8.1.dfsg.P1-4ubuntu0.1) ...
 * Starting domain name service... bind9                                                                                                                                                                                                     /usr/sbin/named: error while loading shared libraries: liblwres.so.80: cannot open shared object file: Permission denied
                                                                                                                                                                                                                                      [fail]
invoke-rc.d: initscript bind9, action "start" failed.
dpkg: error processing bind9 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up postgresql-9.1 (9.1.4-0ubuntu12.04) ...
Creating new cluster (configuration: /etc/postgresql/9.1/main, data: /var/lib/postgresql/9.1/main)...
Can't exec "/usr/lib/postgresql/9.1/bin/initdb": Permission denied at /usr/bin/pg_createcluster line 71.
Error: Could not open /etc/postgresql/9.1/main/start.conf for writing: Permission denied
Can't exec "/bin/sh": Permission denied at /usr/bin/pg_createcluster line 464.
Error: initdb failed
Error: could not create default cluster. Please create it manually with

  pg_createcluster 9.1 main --start

or a similar command (see 'man pg_createcluster').
update-alternatives: using /usr/share/postgresql/9.1/man/man1/postmaster.1.gz to provide /usr/share/man/man1/postmaster.1.gz (postmaster.1.gz) in auto mode.
Errors were encountered while processing:
 bind9
E: Sub-process /usr/bin/dpkg returned an error code (1)



I performed a security update related to Bind ( USN-1462-1 ) using ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
``` before I performed the PostgreSQL install.

I have also tried to remove the failed package using ```
sudo apt-get --pruge remove postgresql-9.1
``` that also fails with a message related to bind.

Please assist?

---

### Post by kendyxing on 2013-03-12
> **hendrel said:**
> When I try to install PostgreSQL 9.1 using ```
sudo apt-get install postgresql-9.1
``` I get the following error message:




I performed a security update related to Bind ( USN-1462-1 ) using ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
``` before I performed the PostgreSQL install.

I have also tried to remove the failed package using ```
sudo apt-get --pruge remove postgresql-9.1
``` that also fails with a message related to bind.

Please assist?
i have the same problem with bind9. i looked "history",and no Permission exception&#65292;I also found that I installed the software will be prompted&#65306;/usr/sbin/named: error while loading shared libraries: liblwres.so.80: cannot open shared object file: Permission denied&#65281;  Of course&#65292;i changed "liblwres.so.80" with "chmod 755 /usr/lib/liblwres.so.80".And get the same answer&#12290;

is this a bug &#65311; how can i fix it &#65281;

---

### Post by slickymaster on 2013-03-12
Have you tried to purge bind9 and then reinstall it:
```
sudo apt-get purge bind9
sudo apt-get install bind9
```

You can be facing some errors with one of the binaries started by **/etc/init.d/bind9**

---

### Post by kendyxing on 2013-03-12
yes.and the same answer.

---

### Post by kendyxing on 2013-03-12
> **hendrel said:**
> When I try to install PostgreSQL 9.1 using ```
sudo apt-get install postgresql-9.1
``` I get the following error message:




I performed a security update related to Bind ( USN-1462-1 ) using ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
``` before I performed the PostgreSQL install.

I have also tried to remove the failed package using ```
sudo apt-get --pruge remove postgresql-9.1
``` that also fails with a message related to bind.

Please assist?
good news ! I changed the permissions of the root directory file &#12290; and  OK...you can try with 

chmod 755 / *

---

