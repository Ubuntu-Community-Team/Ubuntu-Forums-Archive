---
title: "disk changed from hd0 to hd1 in grub 0.97"
date: 2011-04-26
forum: Server Platforms
---

### Post by probablyrobots on 2011-04-26
Hi Folks,

We had a server failure this morning because grub was throwing error 15 (file not found). We discovered that the disk had changed names from hd0,0 to hd1,0. Making the appropriate replacements in menu.lst fixed the problem, but I'm still wondering what could have caused the spontaneous name change.

here are some other possibly related tidbits:
* the server had been down because of a power loss, but it is behind a UPS so i doubt there is any electrical damage
* eth0 also temporarily failed but the system failed over to eth1

My current theory is that when the bios was configuring the hardware the loss of eth0 shuffled around the addresses of the remaining hardware on the pci bus, which somehow caused the hd0/hd1 confusion. The problem is that everything i've read ([http://ubuntuforums.org/archive/index.php/t-160035.html](http://ubuntuforums.org/archive/index.php/t-160035.html)) says that the drive assignment should be based on the way the disk is connected to the motherboard (which in this case didn't change)

Can anyone explain why the mapping changed? Any insight would be greatly appreciated.

Thanks!

---

