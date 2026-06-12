---
title: "Setup.sh impossible situation"
date: 2015-08-10
forum: Server Platforms
---

### Post by Andrew_McCann on 2015-08-10
I have spent two days trying to install OMSA (OpenManage Server  Administrator) for managing my Dell Poweredge 2850. I was given the  wrong version by Dell for my version of Linux and this version is now  'stuck' because when I now try to use the correct version of setup.sh I  get an error which says there is already an installation running, even  after I've rebooted the server. It says if I want to continue anyway the  just delete the lock file in var/lock/LCK..server-admin/setup.sh.o  WHICH I CANT FIND ANYWHERE!!!! So I'm totally stuck!!! PLEASE HELP!!!  :-) I see no way of clearing this lock and getting the correct version  installed, this must be a common problem??

---

### Post by howefield on 2015-08-10
> **howefield said:**
> Thread moved to the "*Server Platforms*" forum.

PS. What is your version of linux ?

---

### Post by Andrew_McCann on 2015-08-10
Ububtu 12.04.05 LTS Linux 3.5.0-54-generic i686

---

### Post by LHammonds on 2015-08-10
It might be hidden.  Make sure to list file with the -la option.

Example:
```
ls -la /var/lock/whatever
```

Also, it might not be telling you the exact filename.  If you don't see it at the highest level, go back one directly and list all files/folders and see if there is something named very similar (may or may not change frequently).  Keep going back a level until it is clear that it is not anywhere in the path of the original report.

LHammonds

---

### Post by cj13579 on 2015-08-10
You could do something a little more rustic using find:

```
find /var/lock -type -f -name setup.sh.o
```

---

### Post by Andrew_McCann on 2015-08-10
Thank you both, but I did search this way for all wildcards including hiddens and nothing, i'm convinced there's a flag somewhere and no such lock file at all.

---

### Post by Andrew_McCann on 2015-08-13
UPDATE - So Dell set me a link to a 1.2Gb download which allowed me to create a USB boot and run this on the server and clear the log file! Worked like a charm, and thank you all for your help!

---

