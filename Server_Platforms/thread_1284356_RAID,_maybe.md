---
title: "RAID, maybe?"
date: 2009-10-06
forum: Server Platforms
---

### Post by awhogan on 2009-10-06
I've just taken over administration of a server I didn't build (8.04). Can anybody tell me how to check if this thing is running RAID? I can see that it is using Logical Volume Management, but I really don't know about RAID.

---

### Post by fjgaude on 2009-10-06
If it is running software raid, **mdadm**, then this command would be useful:

```
cat /proc/mdstat
```

---

### Post by awhogan on 2009-10-07
Here's the output:
```

Personalities : 
unused devices: <none>

```

fdisk shows this:```


Disk /dev/sda: 598.8 GB, 598879502336 bytes
255 heads, 63 sectors/track, 72809 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1052     8388608   8e  Linux LVM
/dev/sda3   *        1053        1078      208845   83  Linux
/dev/sda4            1079       72809   576179257+   f  W95 Ext'd (LBA)
/dev/sda5            1079        1340     2104483+  82  Linux swap / Solaris
/dev/sda6            1341       72809   574074711   8e  Linux LVM

Disk /dev/dm-0: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 4294 MB, 4294967296 bytes
255 heads, 63 sectors/track, 522 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/dm-2: 3221 MB, 3221225472 bytes
255 heads, 63 sectors/track, 391 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-2 doesn't contain a valid partition table

Disk /dev/dm-3: 3221 MB, 3221225472 bytes
255 heads, 63 sectors/track, 391 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-3 doesn't contain a valid partition table

Disk /dev/dm-4: 7516 MB, 7516192768 bytes
255 heads, 63 sectors/track, 913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-4 doesn't contain a valid partition table

Disk /dev/dm-5: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-5 doesn't contain a valid partition table

Disk /dev/dm-6: 107.3 GB, 107374182400 bytes
255 heads, 63 sectors/track, 13054 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-6 doesn't contain a valid partition table

Disk /dev/dm-7: 214.7 GB, 214748364800 bytes
255 heads, 63 sectors/track, 26108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-7 doesn't contain a valid partition table
```

---

### Post by fjgaude on 2009-10-07
Looks like you have hardware raid... if you boot the machine a raid BIOS should show during the process... it will come up before the main BIOS.

---

### Post by trundlenut on 2009-10-08
If it isn't already installed you can install Dell OMSA which will allow to access things like the hardware raid controller.  You can get it running through a web interface but there are also command line tools included with it.

I don't have the appropriate links for how to install OMSA on Ubuntu but I found it from the forums, try a search.

---

