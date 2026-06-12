---
title: "Formatting Extra Drive"
date: 2005-05-04
forum: Server Platforms
---

### Post by bazh on 2005-05-04
I've got a 300gb sata drive (internal) conncected up and ready to format.

This will be used as a hot swop backup drive (ive got 2)

At the moment the drive is free space, whats the best way to format it and how? (primary/logical etc.)

Do i need swop space on this drive?

The machine has 128mb ram.

I'll be using the CLI, so mke2fs or cfdisk are fine.

---

### Post by nad on 2005-05-04
If you are looking to create a linux software raid1 (mirror) with your two disks, please begin with the md man page.

---

### Post by bazh on 2005-05-04
Sorry, should have made this clearer.

I've got an 18gb scsi drive as the OS drive, and the hot swap 300gb drives for file backups.

Will be keeping a weeks worth on disk, the using the next disk.

I've got a internal drive cage, which allows me to swop the sata disks when i need to.

---

### Post by nad on 2005-05-04
I'm still not entirely clear as to what you wish to do.

No, it does not need a swap partition. Logical partitions are simply a method of overcoming the 4 primary partition limit of an x86 system. Maybe you wish to have a partition for each day of the week. It is your backup solution. Are you going to be using backup software? Automated? Just copying files over?

---

### Post by bazh on 2005-05-04
Going to mount samba shares, and rsync these to the backup drive.

I've a test script in place.

I was just asking, HOW TO format the drive, commands etc.

---

### Post by nad on 2005-05-04
Ahhh...

You already know about cfdisk. You also have fdisk, sfdisk and parted. You may use any of these, as well as the gui frontends for parted; gparted and qtparted.

As for filesystem formatting; you've got several to choose from. For large directories of large files I prefer xfs: mkfs.xfs . It is an extremely fast journaling file system from IBM with very good support. Ext3, journalled ext2, is a good general purchase filesystem and the default for an ubuntu install: mkfs.ext3 . The man pages go by the same names.

---

### Post by alastair on 2005-05-04
XFS is SGI technology, not IBM :-)

[http://oss.sgi.com/projects/xfs/](http://oss.sgi.com/projects/xfs/)

---

