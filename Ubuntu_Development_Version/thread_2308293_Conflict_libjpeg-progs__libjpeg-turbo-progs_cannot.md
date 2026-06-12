---
title: "Conflict: libjpeg-progs / libjpeg-turbo-progs cannot coexist?"
date: 2016-01-01
forum: Ubuntu Development Version
---

### Post by syntaxerror74 on 2016-01-01
Happy new year everybody!

Xenial (Alpha 1) upgrade done TODAY (as announced on New Year's Eve, cf. release schedule).
Everything worked fine, up to the point when it came to libjpeg-(turbo)-progs:

*(Precondition: Removed BOTH libjpeg-progs and libjpeg-turbo-progs from my system to be sure there are no relicts that might cause trouble.)*

```
user@my-lubuntubox:~$ sudo apt-get install libjpeg-progs 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  libjpeg-progs
0 to upgrade, 1 to newly install, 0 to remove and 1 not to upgrade.
Need to get 0 B/70,8 kB of archives.
After this operation, 185 kB of additional disk space will be used.
(Reading database ... 315225 files and directories currently installed.)
Preparing to unpack .../libjpeg-progs_1%3a9a-2ubuntu1_i386.deb ...
Unpacking libjpeg-progs (1:9a-2ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libjpeg-progs (1:9a-2ubuntu1) ...
```

```
user@my-lubuntubox:~$ sudo apt-get install libjpeg-turbo-progs
Reading package lists... Done
Reading state information... Done
The following NEW packages will be installed
  libjpeg-turbo-progs
0 to upgrade, 1 to newly install, 0 to remove and 1 not to upgrade.
Need to get 54,1 kB of archives.
After this operation, 182 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu xenial/universe i386 libjpeg-turbo-progs i386 1.3.0-0ubuntu2 [54,1 kB]
Fetched 54,1 kB in 1s (39,3 kB/s)        
Selecting previously unselected package libjpeg-turbo-progs.
(Reading database ... 315245 files and directories currently installed.)
Preparing to unpack .../libjpeg-turbo-progs_1.3.0-0ubuntu2_i386.deb ...
Unpacking libjpeg-turbo-progs (1.3.0-0ubuntu2) ...
dpkg: error processing archive /var/cache/apt/archives/libjpeg-turbo-progs_1.3.0-0ubuntu2_i386.deb (--unpack):
 trying to overwrite '/usr/bin/cjpeg', which is also in package libjpeg-progs 1:9a-2ubuntu1
Errors were encountered while processing:
 /var/cache/apt/archives/libjpeg-turbo-progs_1.3.0-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Looks to me that these packages are **mutually exclusive** - only one can be installed at a time.
However, my package server has listed both of them, and that is what seems to be causing trouble here.

---

### Post by ian-weisser on 2016-01-02
I would file a bug.
libjpeg-progs claims in it's Debian control file to be replaced by libjpeg-turbo-progs, but the version number in libjpeg-turbo-progs' control file may be too low.

---

### Post by mc4man on 2016-01-02
One (turbo) is a fork, not an upgrade. As you've surmised only one or the other can be installed at a time as they both provide the same named binaries.
So just install whichever version you prefer or possibly  need (due to a dep

---

