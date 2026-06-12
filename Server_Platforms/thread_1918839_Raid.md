---
title: "Raid"
date: 2012-02-01
forum: Server Platforms
---

### Post by supplysider on 2012-02-01
[SIZE=3][FONT=Times New Roman]Considering the purchase of a 24 bay server box for a RAID 1 setup but I have a few questions.  I would start out small with 4 HD’s @ 3TB’s each creating a 6 TB drive.  [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]My questions are:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Which would be preferable for such an undertaking, SCSI or SATA?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]If I eventually populate all 24 bays, will existing data be fine, overwritten or the new drives just indexed at the end?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]If I add a second 24 bay server and fully populate it, can it be combined to create one logical drive?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Any recommendations on an adapter card to accomplish this? [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]And lastly, I’m trying to store loads of video.  Perhaps there is a better way of accomplishing this.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Thanks.[/SIZE][/FONT]

---

### Post by rubylaser on 2012-02-02
I assume you mean RAID10, because 4 disks in a RAID1 would give you 3TB of space. I would use mdadm, but the problem you'll quickly run into is a good filesystem to use on this because ext4 currently maxes out at 16TB and after all of the corruption problems I've experienced on large volumes, I won't touch XFS at all anymore.  Personally, I would be using ZFS for this, and set up a few vdevs on each machine to allow for easy expansion.

If you like the idea of mirroring, you can add (2) disk mirrors as you added hard drives.  (12) 2 disk mirrors would give you 36TB of storage.  ZFS will automatically grow the filesystem to take advantage of the new storage space.  

Personally, in a 24 bay server with 3TB drives, I'd be doing (3) 8 disk raidz2 vdevs (you'd end up with 6 parity drives in the server).  That would give you 54TB of usable, very safe storage in one box.  I wouldn't bother trying to combine the arrays, you can do that on the client with something like mhddfs or with video client software.

I would be doing this project with SATA drives. If you add drives your array will safely grow as you go.  I'd go with something like this for hardware.

```

**[CASE]**NORCO RPC-4224
**[MOBO]**SUPERMICRO MBD-X9SCM-F-O
**[CPU**]Intel Xeon E3-1230
**[RAM]**KVR1333D3E9SK2/8G <---Two of these (16GB of RAM, ZFS loves to have lots of RAM)
**[HBA]**IBM M1015 <---Three of these flashed with LSI 9211-8i IT firmware(24 SATA ports total, add these as you add disks)

```

Those parts won't be super expensive, but that will be a rock solid base to start from.  Your disk are what will use the bulk of your budget in the long run.  Hopefully, you'll get some other ideas, but that's a start.

---

### Post by kevdog on 2012-02-02
Id just spend some dollars, go out and get myself a 3ware raid card (does it all in hardware, not software), and do a RAID5 or RAID6.  I mention 3ware -- not because I work for them, but because they make hardware with drivers for all major OS's -- windows, linux.  In addition the raid is done with hardware so its a lot quicker.

---

### Post by codmate on 2012-02-03
3Ware are good, but Adaptec also make true hardware RAID cards with high performance.

3Ware are generally preferred by those who like the web interface some of their products provide.

Regardless of which manufacturer you go for; I'd go with buying a large conventional PC case and filling it with 2TB drives and a 2 small SSDs - one for the system disk, one for the system disk backup.
Server drive units are really really hot and noisy. You would have to be crazy (or have sound insulation and air-conditioning in a dedicated server room) to bring one into your house.

You can build your own quiet, unobtrusive NAS much more easily.

I would build two RAID5 arrays across the set of 2TB disks, using one for backup (RAID redundancy is NOT a backup) over rsync. I would always go with LVM2 as the base filesystem. It will ensure the NAS has maximum flexibility as you move forward, and solve any problems with filesystem size limits before they start.

---

### Post by rubylaser on 2012-02-03
> **kevdog said:**
> Id just spend some dollars, go out and get myself a 3ware raid card (does it all in hardware, not software), and do a RAID5 or RAID6.  I mention 3ware -- not because I work for them, but because they make hardware with drivers for all major OS's -- windows, linux.  In addition the raid is done with hardware so its a lot quicker.

Alot quicker than ZFS?  Have you ever used ZFS with a decent amount of RAM?  I have an Openindiana server at work with 48GB of RAM (ARC) and  ( 8 ) 7200 RPM SATA drives in raidz2 (the equivalent of RAID6), I get around 600 MB/s reading and writing to the array.  A hardware controller isn't going to be any faster than that with a similar number of disks and type. Also, I wouldn't even think of recommending RAID5 if the array could potentially contain 24 disks in the future. One parity disk with a volume that large would be crazy.  

Finally, going the software route you're not relying on a hardware card that if it dies in a year or two you may be SOL if you can't find a replacement. ZFS currently works in Solaris, Openindiana, Nextana, Linux, and FreeBSD (version 28 pools).  That coupled with bit rot protection on a huge filesystem is a definite plus.

---

### Post by rubylaser on 2012-02-03
> **codmate said:**
> 3Ware are good, but Adaptec also make true hardware RAID cards with high performance.

3Ware are generally preferred by those who like the web interface some of their products provide.

Regardless of which manufacturer you go for; I'd go with buying a large conventional PC case and filling it with 2TB drives and a 2 small SSDs - one for the system disk, one for the system disk backup.
Server drive units are really really hot and noisy. You would have to be crazy (or have sound insulation and air-conditioning in a dedicated server room) to bring one into your house.

You can build your own quiet, unobtrusive NAS much more easily.

I would build two RAID5 arrays across the set of 2TB disks, using one for backup (RAID redundancy is NOT a backup) over rsync. I would always go with LVM2 as the base filesystem. It will ensure the NAS has maximum flexibility as you move forward, and solve any problems with filesystem size limits before they start.

LVM2 is not a filesystem, it's a logical volume manager, you'd still need a filesystem on top of it. You'll still need a filesystem and the limits are still an issue.

The Norco cases with the replacement 120mm fan backplanes are not very loud at all.  I would suggest a mirrored OS drive, and buy a third for a system image.  

Backing up TB of storage in a home application can become a very expensive endeavor for most people, so I'd suggest more parity than RAID5 if you're going to grow to more than 8 disks in the future.

---

### Post by codmate on 2012-02-03
> **rubylaser said:**
> I wouldn't even think of recommending RAID5 if the array could potentially contain 24 disks in the future. One parity disk with a volume that large would be crazy.

RAID5 has distributed parity blocks, so I'm not sure where you're coming from.

---

### Post by codmate on 2012-02-03
> **rubylaser said:**
> LVM2 is not a filesystem, it's a logical volume manager, 

Sure but I like to think of it as a filesystem; since all LVM partitions must be set to the LVM partition type in fdisk. 

I suppose the advantages of LVM2 are precisely that it is not a filesystem though.
> 
you'd still need a filesystem on top of it. You'll still need a filesystem and the limits are still an issue.

1EiB for ext4 might take a while to fill up.
16TiB is the limit for a single file.

Even then, you can simply add to the Volume Group when you run out of space.

---

### Post by rubylaser on 2012-02-03
> **codmate said:**
> RAID5 has distributed parity blocks, so I'm not sure where you're coming from.

Yeah... but you can only lose 1 disk in an array of 24 disks.  Have you ever tried a 24 disk resync?  It takes forever, and the likelihood that another disk fails is pretty high, thus causing the loss of all of your data.  Seems a stupid risk, if you had the money to buy 24 drives to not use at least 2 parity drives (RAID6) or ZFS's raidz2 in multiple vdevs or raidz3(3 parity disks).

---

### Post by rubylaser on 2012-02-03
> **codmate said:**
> Sure but I like to think of it as a filesystem; since all LVM partitions must be set to the LVM partition type in fdisk. 

I suppose the advantages of LVM2 are precisely that it is not a filesystem though.


1EiB for ext4 might take a while to fill up.
16TiB is the limit for a single file.

Even then, you can simply add to the Volume Group when you run out of space.

This is not correct.  Those are the theoritical limits for ext4. Try making a filesystem greater than 16TB. You can't, because e2fsprogs doesn't support volumes greater than 16TB. Do a Google search for "ext4 16tb limit" and you'll understand why this is the case. The only way around this limit is to use [experimental code]("http://blog.ronnyegner-consulting.de/2011/08/18/ext4-and-the-16-tb-limit-now-solved/").  Not something I'd want to do with 50TB+ of my data.

---

### Post by MacUsers on 2012-02-14
[FONT=Arial][SIZE=2][SIZE=2]> **codmate said:**
> RAID5 has distributed parity blocks, so I'm not sure where you're coming from.Well, I have around 300TB of storage (50TB on each server) in RAID6 configuration (considering two (parity disk) is better than one) and it's running just fine. There are two major problems with RAID5:[/SIZE][/SIZE][/FONT][SIZE=2] Even[/SIZE] if a single disk in the array fails, the entire array runs at very high risk, which brings the 2nd problem - it doesn't offers any protection when the first disk dies. So, if a second disk dies before replacing the first one (or before rebuilding the array), you are a dead man. RAID6 addresses those issues (paying the cost towards the longer processing time) but again if the third disk fails in the same fashion, you are dead for second time. But it's most unlikely that three disks will fail at the same time or close to each other. 

If money is not a problem, RAID10 is the safest one to use for any mission critical data. Cheers!!

---

### Post by MacUsers on 2012-02-14
[FONT=Arial][SIZE=2][SIZE=2]> **codmate said:**
> RAID5 has distributed parity blocks, so I'm not sure where you're coming from.Well, I have around 300TB of storage (50TB on each server) in RAID6 configuration (considering two (parity disk) is better than one) and it's running just fine. There are two major problems with RAID5:[/SIZE][/SIZE][/FONT][SIZE=2] Even[/SIZE] if a single disk in the array fails, the entire array runs at very high risk, which brings the 2nd problem - it doesn't offers any protection when the first disk dies. So, if a second disk dies before replacing the first one (or before rebuilding the array), you are a dead man. RAID6 addresses those issues (paying the cost towards the longer processing time) but again if the third disk fails in the same fashion, you are dead for second time. But it's most unlikely that three disks will fail at the same time or close to each other. 

If money is not a problem, RAID10 is the safest one to use for any mission critical data. Cheers!!

---

