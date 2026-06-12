---
title: "Safely remove mdadm RAID superblock"
date: 2011-04-05
forum: Server Platforms
---

### Post by Valise on 2011-04-05
Hi !

I bought a disk to a friend that used it in a raid array, using the entire disk for the raid usage.

To put that disk on service, i used dd-rescue to copy my old disk entirely, and managed to grow and setup a the partition table without losing any data.

My last step was to create a RAID between my entire old disk, with a single partition and a partition of the same size on my new disk.

I ran into some problems, but i manage to somehow fix it imperfectly, but now this setup is working properly.

The problems (and imperfection) came from an issue it did not suspected : at some point, the original RAID superblock of the new disk, living in /dev/sda, resisted to dd-rescue, and so it is scanned by mdadm that tries, obviously unsuccessfully, to use it.

Partition layout :
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00082bbf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3831    30772476    7  HPFS/NTFS
/dev/sda2            3832       66276   501582564+  83  Linux
/dev/sda3           83406       83536     1043456   82  Linux swap / Solaris
/dev/sda4           83536      121602   305760256    f  W95 Ext'd (LBA)
/dev/sda5           83536       91185    61440561    7  HPFS/NTFS
/dev/sda6           91186      121602   244318208   fd  Linux raid autodetect

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006f639

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244197376   fd  Linux raid autodetect

Disk /dev/md0: 250.1 GB, 250058047488 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008ef17

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1       30402   244195328   83

``` mdadm --examine --verbose  --scan
```

ARRAY /dev/md0 level=raid5 num-devices=5 UUID=e7151a0c:f703d2a9:f8ffd617:4de83260
   devices=/dev/sda
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=8207da4e:3b5cd80a:2f538ec9:8666be41
   devices=/dev/sdb1,/dev/sda6

```As you can see, mdadm detects a raid superblock on /dev/sda, where it should not.

I repeat : this setup is working properly besides this raid5 declared on sda, so that is shows up here and there. Since it is using the same device name that my other, proper raid setup, i don't know how to deactivate it since mdadm uses the /dev/mdx name to identify arrays...

Is there any way i could fix it without disrupting my sda partition table ?

---

### Post by rubylaser on 2011-04-05
You should run an 
```
mdadm -E /dev/sda
```
to see what metadata version was used on the old array. If it's 0.90, you should be able to zero the superblock with mdadm.
```
mdadm --zero-superblock /dev/sda
```

---

### Post by Valise on 2011-04-06
I saw the --zero-superblock operation, i was afraid to would break my partition table, so that i was wondering if there were another option.

I had to reboot on a live cd, and it worked perfectly, thanks a lot !

---

### Post by rubylaser on 2011-04-06
No problem, glad to be of service :)

---

### Post by Silver Surfer on 2011-06-03
n/t - please remove

---

