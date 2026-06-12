---
title: "Growing GPT/EFI flagged partition"
date: 2009-02-21
forum: Server Platforms
---

### Post by drunkn on 2009-02-21
Hi

So I just added a new 1TB drive to my raid6(hardware). 

In /proc/partitions the dev is shown as having the extra space availble:


major  minor #blocks      name
8       0    6835937024   sda
8       1    5859374558   sda1

At first I was trying to do just xfs_grow /dev/sda1 but then I realized I needed to grow the partition first. This is where the problem lies...:


/mnt/<removed># fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 6999.9 GB, 6999999512576 bytes
255 heads, 63 sectors/track, 851034 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39c8dc72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      267350  2147483647+  ee  EFI GPT


How do I grow this so I can then grow the xfs?

Thanks

---

### Post by handy on 2009-02-21
You should get better help in the Server Platforms sub-forum.

I've asked the mod's to move your thread there.

---

### Post by Brazen on 2009-02-21
use the "parted" command.  Get information on it with "man parted"

---

### Post by drunkn on 2009-02-24
Got it to work! For anyone searching and comes across this, simply upgrading to Ubuntu 8 (I was using Ubuntu 7) made it work. I assume it's because of the updated parted (1.8.1 vs 1.7.1)

Thanks

---

