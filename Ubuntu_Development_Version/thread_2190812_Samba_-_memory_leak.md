---
title: "Samba - memory leak"
date: 2013-11-29
forum: Ubuntu Development Version
---

### Post by Doug S on 2013-11-29
Hi Everyone,

I have been getting this message:```
no talloc stackframe at ../source3/param/loadparm.c:4831, leaking memory
```On one real i386 Trusty server, and two i386 Trusty VMs.
I found [a debian bug report]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=728666"), which seems to suggest that this message is a Samba problem. I have been having other grief with my VM's, (they do not shutdown is the main issue), and I don't know if the issues are related. I haven't had this message on my 64 bit 14.04 VM, but I also haven't used it for several days.

I was also getting these messages:```
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
```on the one i386 computer that I had updated from 13.10 to 14.04, but I got rid of them by converting my previous smb.conf file to the newer format (summary: the related lines are commented out now).

I am just wondering if others, that use Samba, have seen this message?

Edit: I brought my 14.04 64 bit VM up to date, and now it gives the same message.

---

### Post by Random03 on 2013-12-11
I have the same issue. When I launch commands in command line I get this message:
```
no talloc stackframe at ../source3/param/loadparm.c:4831, leaking memory
```
I'm running Trusty 64bit

---

### Post by Doug S on 2013-12-15
I filed a [bug report]("https://bugs.launchpad.net/debian/+source/samba/+bug/1257186") and it was linked to the [upstream bug report ]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=728666")and the [iso testing tracker]("http://iso.qa.ubuntu.com/qatracker/reports/bugs/1257186").

---

### Post by grizzlysmit on 2014-04-24
I get the same thing with sudo -i:

> 
$ sudo -i
[sudo] password for grizzlysmit: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
14:43:53 root@rakbat:~# 


I'm running Trusty 32 bit


this fixes it:
> 
sudo apt-get remove libpam-smbpass


---

