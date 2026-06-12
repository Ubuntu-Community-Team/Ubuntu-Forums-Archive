---
title: "Disk Size vs. Available"
date: 2010-03-30
forum: Server Platforms
---

### Post by aeonhale on 2010-03-30
Running Ubuntu Server:
# cat /etc/issue
Ubuntu 8.04.3 LTS \n \l


I have 5 physical disks attached to this server, each with 1 partition.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  1.6G   17G   9% /
/dev/sdb1             298G  237G   47G  84% /rsync01
/dev/sdc1             298G  251G   33G  89% /rsync02
/dev/sdd1             298G  283G     0 100% /rsync03
/dev/sde1             298G  220G   64G  78% /rsync04

My question is why is 283GB 100% of /dev/sdd1?  The Size of the disk is 298G but I can only put 283GB of data on this disk.  If you look at /dev/sda1, it will allow me to fill this disk to the full size of the disk (19GB).  Any thoughts?  All disks are EXT3.

Thank you.

---

### Post by psusi on 2010-03-30
By default 5% of disk space is reserved for emergency use by root.

---

### Post by aeonhale on 2010-03-31
Is there a way to change this?  I'm losing 15GB per drive.

Thank you.

---

### Post by psusi on 2010-03-31
Do you REALLY want to fill the whole drive up?  If you do files tend to start getting fragmented.  It is best to not worry about it unless you actually use up all of the space.

---

### Post by aeonhale on 2010-03-31
This server is used from RSYNC (backups) only.  From there, the data gets written to tape (or other media).  I dont mind pushing the limits of the disk(s).  Is there a way to remove this "emergency" reserve?

---

### Post by psusi on 2010-03-31
man tune2fs

---

