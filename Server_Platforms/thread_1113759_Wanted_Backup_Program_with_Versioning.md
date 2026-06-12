---
title: "Wanted: Backup Program with Versioning"
date: 2009-04-02
forum: Server Platforms
---

### Post by linorics on 2009-04-02
Hey there I am looking for a program to backup files from one disk to another that supports versioning. Does anyone know of one that is text or web based. I'm really only looking for simple functionality. 

Setup
Raid5 Share 1TB   md0
Raid1 Backup 1TB  md1

All I need it to do, id to copy all the files from md0 to md1. Also because the files are mostly OpenOffice files there is a requirement for versioning.

Any ideas or thoughts?

---

### Post by bluefrog on 2009-04-02
rdiff-backup

---

### Post by hyper_ch on 2009-04-02
I don't know if I understand correctly.

OOo has a versioning feature in there. If you just backup the according odf file then the OOo versioning inside is still there. Do you mean this?

---

### Post by fballem on 2009-04-02
There's a gui based program in the repositories called sbackup that I have used in the past. There is some information about the program here: [http://sbackup.wiki.sourceforge.net/](http://sbackup.wiki.sourceforge.net/)

In order to access the program, you will have to enable the universe repositories. If you have not already done so, open System > Software Sources. On the Ubuntu Sources tab, select the Community-maintained Open Source software box. The attached screenshot shows the correct setting.

sbackup will backup and restore to a hard drive. I have used it in the past to backup to an external USB drive. This may meet your needs.

Regards,

---

### Post by n.l.o on 2010-05-11
Bump

Anyone found any interesting programs (except the CL python program rdiff-backup)?

---

### Post by iponeverything on 2010-05-11
Using rsync with a file system that supports snapshots, like btrfs, might work for you.

---

### Post by HermanAB on 2010-05-11
Look at Rbackup and Dervish.

---

### Post by n.l.o on 2010-05-11
After some heavy digging, I found something right under my nose.
Back-In-Time ([http://backintime.le-web.org/](http://backintime.le-web.org/))

Anybody used this?

Magnus

---

