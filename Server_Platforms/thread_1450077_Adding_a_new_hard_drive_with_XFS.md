---
title: "Adding a new hard drive with XFS"
date: 2010-04-08
forum: Server Platforms
---

### Post by Loki57701 on 2010-04-08
I need some help on this one. I added an second internal hard drive to my file server, a 500GB WD. I want to use this drive as the primary storage drive for my file server, and I want to format it with XFS. 

I've found some guides showing me how to add hard drives, but they didn't really fit what I want to do.

When I run *fdisk -l* this is what I get

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001af4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14412   115764358+  83  Linux
/dev/sda2           14413       14593     1453882+   5  Extended
/dev/sda5           14413       14593     1453851   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```If one of you linux guru's out there could show me what I need to do I would really appreciate it!

---

### Post by tgalati4 on 2010-04-08
apt-cache search xfs

There's a program called xfsprogs:

sudo apt-get install xfsprogs

man xfsprogs

There may be a kernel module that you have to load to get the operating system to recognize the xfs file system.  I'm really not sure.

What is the advantage of using xfs?  ext2,3 and 4 work pretty well depending on your needs:  ext2 for static storage (music & videos), ext3 with journaling for power-outage and program-crash protection, ext4 slightly better retrieval performance and small-file handling.

---

### Post by Loki57701 on 2010-04-08
Well, basically I heard XFS was a nice file system from some people I've worked with. If I don't really need to use XFS than I won't. 

I suppose ext2 or 3 is the file system I would need since I would only be storing pictures and maybe a few videos. 

How would I go about formatting the new drive with ext2?

I'm new to this, so I'm unfamiliar with the process of adding a new drive to linux. I appreciate your help.

---

### Post by Vegan on 2010-04-08
Actually ext4 is now used more widely as it supports huge file systems and is stable on my server, so I suspect its going to replace other file systems over time as more shops replace old servers.

---

### Post by tgalati4 on 2010-04-08
For static storage, ext2 is fine.  If you are moving files around a lot, or doing video editing and using that drive as a scratch disk, then you would need ext3 or ext4.

For simple write once, read many, you can't beat ext2 for capacity and low overhead.

man mkfs

sudo gparted /dev/sdb

Create a few partitions, select ext2 for type, then check the format box and apply.  

Reboot and make a few directories on one of your partitions and start dumping files.

Here's info on xfs:

[http://en.wikipedia.org/wiki/XFS](http://en.wikipedia.org/wiki/XFS)

It can handle really large files.

Here's ext2:

[http://en.wikipedia.org/wiki/Ext2](http://en.wikipedia.org/wiki/Ext2)

Ext3 is ext2 with journaling.

I don't know if gparted can format xfs file systems, you will have to run the program and see if that option is available.  Personally, I would stick with ext2 on a static data partition, and ext3 on a scratch or data_dump partition.

You can mix and match filesystems on one disk.  Each partition can have a different file system.  You could have ext2, ext3, ext4, and xfs partition all on the same physical disk.

---

### Post by Loki57701 on 2010-04-08
**EDIT**:* I was writing this post before I seen your post tgalati4.*

Ok, I'm not sure I did this right.

I did:

```

sudo mkdir /mnt/share

``````

sudo chmod 777 /mnt/share

``````

sudo mkfs.ext3 /dev/sdb

``````

sudo nano /etc/fstab

```Added the following to my fstab
```

/dev/sdb    /mnt/share    ext3    defaults    0    0

``````

sudo mount -a

```I restarted the server and ran **fdisk -l** after all this and got:
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001af4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14412   115764358+  83  Linux
/dev/sda2           14413       14593     1453882+   5  Extended
/dev/sda5           14413       14593     1453851   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table


```I'm not sure why linux is saying the drive doesnt contain a valid partition..

Just out of curiosity I added the following to my **/etc/samba/smb.conf** file
```

[share]
        path = /mnt/share
        browseable = yes
        guest ok = yes
        read only = no
        create mask = 0775


```After I restarted SAMBA, I was able to connect to the share from my other computers.

So why does linux say the drive doesnt have a valid partition, but I can share the drive through SAMBA, and see it from my other computers, and read/write it?

A lot of question I know.. sorry

---

### Post by Loki57701 on 2010-04-08
Ok, I see what I did. I didn't make a partition table for the new drive. 

--more research.. yay

---

### Post by tgalati4 on 2010-04-08
Yes, you need to partition the drive with gparted or cfdisk.  Then linux will read its partition table and all will be write with the world.

---

