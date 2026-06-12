---
title: "mdadm failing to create RAID 5 HELP!!!"
date: 2008-11-12
forum: Server Platforms
---

### Post by Mercedes300 on 2008-11-12
I'm trying to create a RAID 5 array with 4 1TB SATA HDD. Following [this]("http://bfish.xaedalus.net/?p=188") guide, I formated and flagged the partitions as RAID with gparted.

This is the output of $sudo fdisk -l

```
user@computer:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003f0d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00025dd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00057108

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00024d81

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc4946615

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       29164   234259798+  83  Linux
/dev/sde2           29165       30401     9936202+   5  Extended
/dev/sde5           29165       30401     9936171   82  Linux swap / Solaris
user@computer:~$ 

```

This is per the guide. As you can see, it doesn't think sdc1 and sdd1 exist... very annoying!

```
user@computer:~$ sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=4 /dev/sda1 /dev/sdb1 dev/sdc1 dev/sdd1 
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: /dev/sda1 appears to contain an ext2fs file system
    size=976760000K  mtime=Wed Nov 12 13:09:36 2008
mdadm: /dev/sdb1 appears to contain an ext2fs file system
    size=976760000K  mtime=Wed Dec 31 19:00:00 1969
mdadm: Cannot open dev/sdc1: No such file or directory
mdadm: Cannot open dev/sdd1: No such file or directory
mdadm: create aborted
user@computer:~$ 

```

I also created and added the line "DEVICE partitions" to /etc/mdadm/mdadm.conf and executed the command
```
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

Why doesn't it see dev/sdc1 or dev/sdd1? I can mount both partitions, and they both have a Lost+Found directory in them.

All help is much appreciated

---

### Post by Mercedes300 on 2008-11-13
OK, working threw this, I found that I can just add the two devices that work, and grow the array later with this [guide]("http://scotgate.org/?p=107"). I'll keep you updated as things progress.

cheers! :KS

---

### Post by obg123 on 2008-11-13
Come on... Why do you think it does not find dev/sdc1 and dev/sdd1?

I would try /dev/sdc1 and /dev/sdd1 if I were you... ;)

---

### Post by colskinet on 2008-11-13
> **obg123 said:**
> Come on... Why do you think it does not find dev/sdc1 and dev/sdd1?

I would try /dev/sdc1 and /dev/sdd1 if I were you... ;)

Bingo, I had exactly the same problem the other night, baffled me for a whole hour!

---

### Post by fjgaude on 2008-11-13
> **colskinet said:**
> Bingo, I had exactly the same problem the other night, baffled me for a whole hour!

Well, tell us how you fixed it, or how you are now doing.

---

### Post by Mercedes300 on 2008-11-13
!!!!!!!! NO WAY!  How could I be so stupid! I just kept recalling the command instead of re-typing it!

Man, that was a big goof on my part!

thanks guys for pointing out my obvious blunder.

---

### Post by fjgaude on 2008-11-13
Yes, /dev/sda1 is not dev/sda1, and /dev/sda1 is not /dev/sda. <smile>

---

