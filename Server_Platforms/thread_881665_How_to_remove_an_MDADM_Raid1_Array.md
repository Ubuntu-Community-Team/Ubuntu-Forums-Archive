---
title: "How to remove an MDADM Raid1 Array"
date: 2008-08-06
forum: Server Platforms
---

### Post by sploutch on 2008-08-06
Hi!

I try to install Ubuntu Server on RAID1-Software but I got somethings very strange...

Before this problem, I had install the Ubuntu Server with no problem. 

```
$ sudo fdisk -l
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008613e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         122      979933+  83  Linux
/dev/sda2             123         244      979965   82  Linux swap / Solaris
/dev/sda3             245        2068    14651280   fd  Linux raid autodetect
/dev/sda4            2069      121601   960148822+  fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008a22d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         122      979933+  83  Linux
/dev/sdb2             123         244      979965   82  Linux swap / Solaris
/dev/sdb3             245        2068    14651280   fd  Linux raid autodetect
/dev/sdb4            2069      121601   960148822+  fd  Linux raid autodetect

Disk /dev/md0: 15.0 GB, 15002828800 bytes
2 heads, 4 sectors/track, 3662800 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1: 983.1 GB, 983192305664 bytes
2 heads, 4 sectors/track, 240037184 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

```

But after reboot, I can't boot... /dev/md0 doesn't exist ! And now I can't delete the md0 and md1 to reinstall it!?!?

I already read this archive ( [http://ubuntuforums.org/showthread.php?p=2459683](http://ubuntuforums.org/showthread.php?p=2459683) ), but when I do this command :
```
sudo mdadm --zero-superblock /dev/sda
```
I get this message:
```
mdamd: Unrecognised md component device - /dev/sda
```

How can I delete it? Thanks to help me...
Sploutch.

---

### Post by fjgaude on 2008-08-06
First off, the /dev/sda is not where the superblocks are, but on /dev/sda3 and 4.

You might wish to read, study these:
[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
   then study /usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

Good luck!

---

### Post by Krupski on 2008-08-07
> **sploutch said:**
> Hi!

I try to install Ubuntu Server on RAID1-Software but I got somethings very strange...

Before this problem, I had install the Ubuntu Server with no problem. 

```
$ sudo fdisk -l
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008613e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         122      979933+  83  Linux
/dev/sda2             123         244      979965   82  Linux swap / Solaris
/dev/sda3             245        2068    14651280   fd  Linux raid autodetect
/dev/sda4            2069      121601   960148822+  fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008a22d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         122      979933+  83  Linux
/dev/sdb2             123         244      979965   82  Linux swap / Solaris
/dev/sdb3             245        2068    14651280   fd  Linux raid autodetect
/dev/sdb4            2069      121601   960148822+  fd  Linux raid autodetect

Disk /dev/md0: 15.0 GB, 15002828800 bytes
2 heads, 4 sectors/track, 3662800 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1: 983.1 GB, 983192305664 bytes
2 heads, 4 sectors/track, 240037184 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

```

But after reboot, I can't boot... /dev/md0 doesn't exist ! And now I can't delete the md0 and md1 to reinstall it!?!?

I already read this archive ( [http://ubuntuforums.org/showthread.php?p=2459683](http://ubuntuforums.org/showthread.php?p=2459683) ), but when I do this command :
```
sudo mdadm --zero-superblock /dev/sda
```
I get this message:
```
mdamd: Unrecognised md component device - /dev/sda
```

How can I delete it? Thanks to help me...
Sploutch.

I had a similar problem. I found that the RAID information is stored at the very END of each drive in the array.

So, I used 'dd' with the appropriate 'seek' offset and a block size of 1 gig to copy /dev/zero to the end of the drives.

Note you have to wipe (example) /dev/sda, /dev/sdb, etc... NOT the raid device (/dev/md0).

Then, you can re-create your array any way you like.

-- Roger

---

