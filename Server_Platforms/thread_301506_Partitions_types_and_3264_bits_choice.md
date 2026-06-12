---
title: "Partitions types and 32/64 bits choice"
date: 2006-11-17
forum: Server Platforms
---

### Post by Homer on 2006-11-17
Hello,

What do you use as files system for your Ubuntu server ?  I would want to avoid ext3 since the fsck is very long to do on large files system when the computer didn't unmounted correctly the partition (ie when system crash occurs).

XFS a good choice ?  The server will be used as Web server (php developpements) and database server (MySQL or PostgreSQL).

I read some things about fs fragmentation with XFS.  Will I need to defrag it like on Windows files systems ?

I also read some things about "4k stacks" wich I didn't fully understood.. is it a real problem ?

If XFS is not a good choice, what are other alternatives to ext3 ?

Actually, I would partition my 80GB HD as :
swap 2GB
/ 20GB xfs
/boot 100MB ext3
/tmp 2GB xfs
/home 5GB xfs
/var ~50GB xfs


On an another subject, the server will run on 64 bits enabled CPU.  Should I go with the old well tested 32 bits technology or to the new 64 bits one ?

On a desktop OS, I will not think about this question because of flash, video codecs & co, but on a server, will I have somes problems with the 64 bits ?  Will I have some advantages to use it t?


Thanks !

---

### Post by Homer on 2006-11-20
Nobody ?

---

### Post by Macchi on 2006-11-20
Many scattered comments about your posting:

- Ubuntu 6.06.1 Long Term Support is a very good server!

- I would recommend fewer partitions for your system, but everything depends on the application context for you server. Consider using LVM if you intend to change the size of the partitions in the future. But this has an added cost on complexity and maintenance, thus start preferably without the LVM and reinstall the system later when you can master it.

- The 64 bits version for Ubuntu seem to be very stable, but there might be exceptions for specific devices. It is worth to try since the installation of a Ubuntu server is quite fast and straightforward.

- Normally it is recommended to have as little software as possible and required on a server, but no more that that. Thus no desktop.

- File-system fragmentation is handled automatically by Linux.

- ReiserFS is reported to be very reliable and efficient for a large number of files.

- Use ext2 for a boot partition. Journalling from etx3 does not make sense for a small boot partition. Why not making it approx 256MB in size?

- Swap space could be double the size of the RAM, but there are many opinions on this issue.

- Definitely use a separate home partition if you have many users and/or persistent information. 

- Eventually create a separate partition for bulk storage, that is data will not require the same backup procedures that /home and the system. A typical example is storing music, video, and pictures that have a safe backup somewhere else.

- Consider having a separate spare system partition with a live copy of your system. A server without the graphical desktop manager takes only approx 700MB of space. Thus you could create two partitions (ordinary and reserve) with a few GB each. Install the system on one partition, configure and upgrade the software and then copy the freshly installed system to the other partition. If something happens to your ordinary system you can promptly start from the other partition, copy the reserve system back to the ordinary partition, and restart again with a fresh copy. 
It requires some tweaking with /boot/grub/menu.lst and /etc/fstab.

Good luck and keep in touch!

---

### Post by Homer on 2006-11-20
> **Macchi said:**
> Many scattered comments about your posting:

- Ubuntu 6.06.1 Long Term Support is a very good server!

Yep, it's what I planned to install.

> **Macchi said:**
> - I would recommend fewer partitions for your system, but everything depends on the application context for you server. Consider using LVM if you intend to change the size of the partitions in the future. But this has an added cost on complexity and maintenance, thus start preferably without the LVM and reinstall the system later when you can master it.

I know a little bit LVM because I used it for my personal MythTV box.  But LVM is not supported by all system tools, like partimage for backups/clonning hard drives.

> **Macchi said:**
> - ReiserFS is reported to be very reliable and efficient for a large number of files.

I searched for a while on Google about file systems.  I think I will go with ReiserFS.

> **Macchi said:**
> - Use ext2 for a boot partition. Journalling from etx3 does not make sense for a small boot partition. Why not making it approx 256MB in size?

ext2, why not, but why 256MB ?  My /boot size directory is less than 20MB.  100MB is not enough ?

> **Macchi said:**
> - Definitely use a separate home partition if you have many users and/or persistent information. 

Yes of course.

> **Macchi said:**
> - Eventually create a separate partition for bulk storage, that is data will not require the same backup procedures that /home and the system. A typical example is storing music, video, and pictures that have a safe backup somewhere else.

Will be a corporate server... so no music&video on hard drives :).  Databases data and www root directory will be on /var partition.

> **Macchi said:**
> - Consider having a separate spare system partition with a live copy of your system. A server without the graphical desktop manager takes only approx 700MB of space. Thus you could create two partitions (ordinary and reserve) with a few GB each. Install the system on one partition, configure and upgrade the software and then copy the freshly installed system to the other partition. If something happens to your ordinary system you can promptly start from the other partition, copy the reserve system back to the ordinary partition, and restart again with a fresh copy. 
It requires some tweaking with /boot/grub/menu.lst and /etc/fstab.

The production server will be cloned on a second identical server for testing, but your idea is not bad at all.  I will think about this.


> **Macchi said:**
> Good luck and keep in touch!

Thanks.

---

### Post by mmcmonster on 2006-12-24
Just a quick comment about the partition sizes.  Chances are, most of the data will live in /home, so that should be the large partition.

This is what I use:
/ - 10GB
/swap - 2*RAM
/home - rest

Unless you are running some massive software, 10GB is far more than enough for the entire OS + applications.  A good idea is a second 10GB for a spare /root partition.  Once you know about LFS, that's really the way to do these things, so partition resizing and spanning (across multiple physical disks) can be done.

If you can really afford it, /home (or whereever the data is stored) should be a mirrored partition.

---

