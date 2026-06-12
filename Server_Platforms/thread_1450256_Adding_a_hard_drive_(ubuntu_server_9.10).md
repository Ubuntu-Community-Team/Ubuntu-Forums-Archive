---
title: "Adding a hard drive (ubuntu server 9.10)"
date: 2010-04-08
forum: Server Platforms
---

### Post by Loki57701 on 2010-04-08
I've added a second hard drive to my home file server but I'm unsure how to complete the process.

First I formatted the new drive:

```

sudo mkfs.ext3 /dev/sdb

```After the hard drive was formatted with ext3 I partitioned the drive by:

```

sudo fdisk /dev/sdb

```After the partition table was created for /dev/sdb, I ran **fdisk -l**, and I got:

```

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14412   115764358+  83  Linux
/dev/sda2           14413       14593     1453882+   5  Extended
/dev/sda5           14413       14593     1453851   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61714c3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux


```And that shows the new drive is formatted and partitioned, right?

Now this is where I get a little confused.

I created /share in my root directory with:

```

sudo mkdir share
sudo chmod 777 share

```Than I go to my fstab and add the follwing lines:
```

/dev/sdb        /share          ext2    defaults        0       0


```And in my SMB.conf I added

```

[share]
        path = /share
        browseable = yes
        guest ok = yes
        read only = no
        create mask = 0775


```The problem is, if I reboot my server, the /share is attached to the wrong drive.

---

### Post by dominiquec on 2010-04-08
You need to mount your drive in order to use it.

Assuming you are using the standard Ubuntu desktop: click on Places (top left menu bar, between Applications and System), and you should see your hard drive listed there.

---

### Post by dominiquec on 2010-04-08
Addendum: if you want to mount the hard drive automatically, you have to create a mount point (a directory) and edit /etc/fstab.  You'll need to read elsewhere for detailed instructions.

---

### Post by koenn on 2010-04-09
you're doing it wrong.

you have to partition first, then create filesystem(s) (a.k.a. "format"), then mount.

1- partition : with fdisk or parted
- (delete old partition table)
- (make partition table)
- create partition(s)
- save and quit

2-
the result is that now your disk has partitions, this can be seen by the device names :
disk : /deb/sdb  -> partitions: /dev/sdb1 [/dev/sdb2 /dev sdb/3 ... ]
you make a filesystem in a partition, so mkfs ... /dev/sdb**1**

3- mount the partition(s), eg from /etc/fstab

this page has some more info :
[http://users.telenet.be/mydotcom/howto/linux/disks1.htm](http://users.telenet.be/mydotcom/howto/linux/disks1.htm)

---

