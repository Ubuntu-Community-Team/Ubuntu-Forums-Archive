---
title: "Warnings from /var/log/message"
date: 2009-06-18
forum: Server Platforms
---

### Post by carfield on 2009-06-18
I am using ext4, and I also apply following mount option - [http://pclinuxos2007.blogspot.com/2009/06/tweaks-to-boot-ext4-filesystem.html](http://pclinuxos2007.blogspot.com/2009/06/tweaks-to-boot-ext4-filesystem.html) . However that should not be related as I got similar warning when I use ext3


Jun 18 08:38:26 carfield kernel: [  425.781003] ata1: irq_stat 0x00000040, connection status changed
Jun 18 08:38:26 carfield kernel: [  425.781006] ata1: SError: { PHYInt CommWake DevExch }
Jun 18 08:38:26 carfield kernel: [  425.781012] ata1: hard resetting link
Jun 18 08:38:26 carfield kernel: [  426.504524] ata1: SATA link down (SStatus 0 SControl 300)
Jun 18 08:38:26 carfield kernel: [  426.504530] ata1: EH complete
Jun 18 08:38:27 carfield kernel: [  427.471780] ata1: exception Emask 0x10 SAct 0x0 SErr 0x4060000 action 0xe frozen

But I doesn't find any problem for normal operation

---

### Post by carfield on 2009-06-19
Ok, get the solution, change BIOS setting to disable PATA 

[http://forum.ubuntu-fr.org/viewtopic.php?id=209645](http://forum.ubuntu-fr.org/viewtopic.php?id=209645)

---

