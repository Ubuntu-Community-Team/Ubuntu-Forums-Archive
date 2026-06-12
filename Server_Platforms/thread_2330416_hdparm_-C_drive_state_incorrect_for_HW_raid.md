---
title: "hdparm -C drive state incorrect for HW raid"
date: 2016-07-11
forum: Server Platforms
---

### Post by David_Partridge on 2016-07-11
I have an Adaptec ASR-51245 with 2 x 4TB configured as RAID 1.  All under 14.04 LTS Server

When the drive is active hdparm -C reports:

```
root@Charon:/var/log# hdparm -C /dev/sda1

/dev/sda1:
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 drive state is:  standby
root@Charon:/var/log# 

```

A SATA device on the same controller is correctly reported as active:

```
root@Charon:/var/log# hdparm -C /dev/sdb

/dev/sdb:
 drive state is:  active/idle
root@Charon:/var/log# 

```

Thanks
Dave

---

### Post by David_Partridge on 2016-07-16
Bump?

---

### Post by howefield on 2016-07-16
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by David_Partridge on 2016-07-16
Fine, I'm happy to have the thread there, but more interesting would be to have a fix :)  (I want to put the system in standby with powernap if the RAID is not doing anything).

FWIW 'smartctl -i -n standby' does recognise when the drive is active

---

### Post by MAFoElffen on 2016-07-17
I know that hdparm works with SCSI drives, many SATA drives, many SAS drives and mdadm... but not all command options work with hardware RAID.

I don't have one of those specific controller models, but "-C" is one of those options that doesn't always work with a hardware RAID controller.

---

### Post by volkswagner on 2016-07-17
Sorry I can't give advice here, but I'd like to point out... it seems your commands are not apples to apples.

The first command references a partition, the second references a disk.

---

### Post by MAFoElffen on 2016-07-18
@vlokswagner

LOL-- Good catch. I missed that.

Better to have your eyes on that. Your eyes are qualified to catch that. hdparm works on drives, and not on partitions.

---

### Post by David_Partridge on 2016-07-30
Doesn't make any difference, same error when I choose the logical drive

root@Charon:/home/amonra# hdparm -C /dev/sdb

/dev/sdb:
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 00 00 00 00 20 00                                                                     00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 drive state is:  standby

Dave

---

