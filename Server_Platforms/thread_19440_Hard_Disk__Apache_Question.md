---
title: "Hard Disk / Apache Question"
date: 2005-03-11
forum: Server Platforms
---

### Post by Belldandy on 2005-03-11
Hi Everyone,

First off, I am loving Ubuntu. I am a novice/intermediate user and former Debian user. I absolutely am loving Ubuntu :)

I do, however, have a few questions:

1) I have two SCSI disks in my system. One is not partitioned/formatted at all. How can I partition and format it to be readable by my system? I basically want it to host all of my web files, it doesnt need to be a specific structure, or anything.

2) After I do this, as said above, I want to run my webserver from that hard disk because it is much larger than my primary... in my apache2.conf file, would I then change my server root, virtual hosts, etc to read /mnt/sdb/var/www ?

Thanks in advance!

---

### Post by az on 2005-03-11
1 - man mke2fs
2-  /etc/apache2/sites-enabled  Change the path there.

---

### Post by alastair on 2005-03-12
If you have SCSI disks, check the system logs and see them being probed and found - either :

dmesg

or look in :

/var/log/syslog

You should see SCSI disks e.g. /dev/sda,/dev/sdb for instance.

If a SCSI disk HAS a partition on it, you will also see /dev/sda1 (perhaps).

If you have a SCSI disk /dev/sda, to partition :

1) See what's partitioned already  - list partitions :

sudo fdisk -l /dev/sda

2) Use "fdisk" to partition if required :

sudo fdisk /dev/sda

BE CAREFUL - see "man fdisk".

As stated above - once partitioned (i.e. you have /dev/sda1 say), you can "format" it (i.e. make a filesystem) using something like :

sudo mkfs.ext3 /dev/sda1

(for an ext3 filesystem)

Then mount using :

mount /dev/sda1 /scsidisk

(as an example - make the mount point /scsidisk first)

---

