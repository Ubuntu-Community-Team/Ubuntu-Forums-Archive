---
title: "unable to install gdebi"
date: 2016-11-20
forum: Server Platforms
---

### Post by mbnoimi on 2016-11-20
Hi,

I use Ubuntu Server 14.04 when I tried to install **gdebi** I get this error message and I'm unable to fix it!

```
Setting up colord (1.0.6-1) ...
groupadd: cannot open /etc/group
addgroup: `/usr/sbin/groupadd -g 116 scanner' returned error code 10. Exiting.
dpkg: error processing package colord (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 colord
```

May I get your help please?

---

### Post by mbnoimi on 2016-11-20
BTW, I tried to call the following but I unfortunately it didn't fix it :(
```
# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up colord (1.0.6-1) ...
groupadd: cannot open /etc/group
addgroup: `/usr/sbin/groupadd -g 116 scanner' returned error code 10. Exiting.
dpkg: error processing package colord (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 colord
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ian-weisser on 2016-11-20
Your colord problem seems unrelated to gdebi.

Did you recently try to install/upgrade CUPS or Ghostscript or some other printing-related application?
If so, did it work?

---

### Post by mbnoimi on 2016-11-21
> **ian-weisser said:**
> Your colord problem seems unrelated to gdebi.

Did you recently try to install/upgrade CUPS or Ghostscript or some other printing-related application?
If so, did it work?

I didn't install anything new except **gdebi**!

---

### Post by mbnoimi on 2016-11-23
Guys, May you please help me to fix this issue? My server became unable to upgrade anything :( :( :(

```
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up colord (1.0.6-1) ...
groupadd: cannot open /etc/group
addgroup: `/usr/sbin/groupadd -g 116 scanner' returned error code 10. Exiting.
dpkg: error processing package colord (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libpython3.4-minimal:amd64 (3.4.3-1ubuntu1~14.04.5) ...
Setting up python3.4-minimal (3.4.3-1ubuntu1~14.04.5) ...
Setting up libpython3.4-stdlib:amd64 (3.4.3-1ubuntu1~14.04.5) ...
Setting up python3.4 (3.4.3-1ubuntu1~14.04.5) ...
Setting up libpython2.7-minimal:amd64 (2.7.6-8ubuntu0.3) ...
Setting up python2.7-minimal (2.7.6-8ubuntu0.3) ...
Setting up libpython2.7-stdlib:amd64 (2.7.6-8ubuntu0.3) ...
Setting up python2.7 (2.7.6-8ubuntu0.3) ...
Setting up libpython2.7:amd64 (2.7.6-8ubuntu0.3) ...
Processing triggers for libc-bin (2.19-0ubuntu6.9) ...
Errors were encountered while processing:
 colord
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by kpatz on 2016-11-23
See if the files /etc/group.lock and/or /etc/gshadow.lock exist.  Delete them if they do:```
sudo rm /etc/group.lock
sudo rm /etc/gshadow.lock
```

---

### Post by mbnoimi on 2016-11-23
> See if the files /etc/group.lock and/or /etc/gshadow.lock exist. Delete them if they do:
Both of them aren't exist!

---

### Post by mbnoimi on 2016-12-06
After days of working around this issue I didn't expect to fix it by using a single line!!!

```
apt-get purge colord
```

That's it.. Thanks guys.

---

