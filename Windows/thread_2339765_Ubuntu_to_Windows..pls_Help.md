---
title: "Ubuntu to Windows..pls Help"
date: 2016-10-12
forum: Windows
---

### Post by yomexshow92 on 2016-10-12
I installed Ubuntu 15.10 on HP stream notebook PC 11 as single boot but I want to install windows 8.1 back and have deleted formatted the hard drive using gparted on a Ubuntu live CD and changed the hard drive format to NTFS but Windows installation USB can detect my hard drive and the BIOS is insydeH20 setup utility I dnt knw maybe it RAID,AHCI or IDE

---

### Post by howefield on 2016-10-12
Thread moved to the "*Windows*" sub forum.

---

### Post by Bucky Ball on 2016-10-12
Boot to a live session ('Try Ubuntu')> launch Gparted> delete all partitions> go to 'Devices> Create partition table'. Windows will create, and in this case perhaps prefers to create, its own partitions during install (when you tell it to during install). Try again. Any different?

Licenced version of Windows? If not, anything goes. Won't go into how you created the USB because know little about doing that in Windows, but sure that's working ok? Tried on another machine?

---

