---
title: "Buffalo external drive Raid 1 DriveStation Duo"
date: 2009-04-07
forum: Server Platforms
---

### Post by IQRules on 2009-04-07
It has 2 x 400GB drivers. It has USB and firewire FW400.
Buffalo Tech ships with configuration tool for Windows and Mac not Linux.

# fdisk -l /dev/sdc

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d82f1fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       48641   390700800    f  W95 Ext'd (LBA)
/dev/sdc5               2       48641   390700768+   b  W95 FAT32

# fdisk -l /dev/sdd

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d82f1fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               2       48641   390700800    f  W95 Ext'd (LBA)
/dev/sdd5               2       48641   390700768+   b  W95 FAT32

How to set up Raid 1 or 1+0 with this new toy?

---

