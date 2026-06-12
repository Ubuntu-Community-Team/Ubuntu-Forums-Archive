---
title: "True Hardware RAID5 partition/installation questions"
date: 2009-05-27
forum: Server Platforms
---

### Post by R.Bucky on 2009-05-27
I am configuring a true hardware RAID5 Ubuntu Server box. I have read throughout many forums that the true hardware RAID5 will configure Ubuntu Server without needing to manually edit them during the install. In other words, the installation process is like i would be installing Server on one disk? Would I still need to claim the partitions as RAID, or would the hardware RAID figure it out? 

Any guidance would be appreciated.

---

### Post by Vegan on 2009-05-27
IF you RAID card is supported (driver) then the LVM can work with it fine. It sees the RAID as a single physical disk.

So the punch line is you are laughing.

---

### Post by R.Bucky on 2009-05-27
- Well then, let me hope that I have a supported hardware card! 

thanks again. 

~Mark

---

### Post by windependence on 2009-05-27
It's very easy. When you first boot after you install the card you will see an option to press a key sequence to set up your RAID. Just go into the RAID bios, pick the type of RAID (5) and add your disks and save. Your OS will see it as one big disk. Super easy, AND you can boot from it.

-Tim

---

### Post by R.Bucky on 2009-05-28
server is in my home. i have set the hardware raid5. now, when i install Server, how would i partition the drives? tried using lvm for the first hd and then configuring the remaining two drives as RAID volumes. i keep receiving a grub error 2 code. i have also tried configuring it as a normal ext3 and the remaining 2 hd as RAID also. no dice.

suggestions?

---

