---
title: "Boot from failed software RAID 5"
date: 2015-09-09
forum: Server Platforms
---

### Post by marco114 on 2015-09-09
Hi,
i installed Ubuntu Server 14.04.3 LTS on 3 x 3TB hard drive (2 x RAID 5 volumes - root and swap). The system boot without problem, but when i try to remove one hard drive to test a failure and i restart the system, the display show : GNU GRUB .... Minimal BASH-like line editing is supported..... grub>, and i can't boot.
It seems like GRUB has been installed on all hard drives, but on some of them it's unable to find root partition.
Could you help me ?
Thank you.

---

### Post by slickymaster on 2015-09-09
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by darkod on 2015-09-09
When you were installing and it asked you if you want to boot degraded, did you select Yes or No? If you selected No, it will not boot degraded even when raid5 can work with one member missing.

If you put the disk back and boot, does it boot? (you might need to wait a while if it wants to finish syncing first)

---

