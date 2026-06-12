---
title: "reinstall BIND on Ubuntu server"
date: 2008-07-14
forum: Server Platforms
---

### Post by MatsB on 2008-07-14
I've messed up my bind9 application and would like to reinstall bind9.

I'ver run ```
 sudo apt-get remove bind9 
```
and when i run this ```
 sudo apt-get install bind9 
``` i get this and no startup script or files in /etc/bind:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  bind9-doc resolvconf
The following NEW packages will be installed:
  bind9
0 upgraded, 1 newly installed, 0 to remove and 120 not upgraded.
Need to get 268kB of archives.
After this operation, 762kB of additional disk space will be used.
Get:1 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/main bind9 1:9.4.2-10ubuntu0.1 [268kB]
Fetched 268kB in 0s (707kB/s)
Selecting previously deselected package bind9.
(Reading database ... 59723 files and directories currently installed.)
Unpacking bind9 (from .../bind9_1%3a9.4.2-10ubuntu0.1_i386.deb) ...
Setting up bind9 (1:9.4.2-10ubuntu0.1) ...
Reloading AppArmor profiles Warning: found /etc/apparmor.d/force-complain/usr.sbin.mysqld, forcing complain mode
: done.
```

---

### Post by bluefrog on 2008-07-14
try apt-get remove --purge bind9 and/or apt-get install --reinstall bind9

James Dupin

---

### Post by MatsB on 2008-07-15
> **bluefrog said:**
> try apt-get remove --purge bind9 and/or apt-get install --reinstall bind9

James Dupin

Thx that did the job.

---

