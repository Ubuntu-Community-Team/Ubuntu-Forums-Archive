---
title: "Need help installing XP on my ubuntu laptop"
date: 2008-02-15
forum: Windows
---

### Post by JaggedOne on 2008-02-15
Edit: Problem has been solved, it randomly worked for me once. I didn't even change anything. Im confused but happy.

I am trying to install Windows XP on my dell XPS m1530 running Ubuntu 7.10. I need windows for gaming purposes (wine doesn't cut it). I changed two settings in the BIOS to enable a windows XP install on this laptop that shipped with vista. The first was changing AHCI to ATA. To do that I had to disable flash module memory (or something like that). Once I installed XP on top of ubuntu I was going to use a super grub live cd to repair my master boot record. The only problem is I can't get the windows XP CD to boot. 

I insert the disk into the tray, select boot from CD and after 10 seconds I get to a screen that says "press any key to boot from cd.." At this point the computer is essentially frozen. All I can get it to do is make a bunch internal beeps when I smash the keyboard enough. 

Any help would be greatly appreciated.

Edit: I tried one more thing that did not work. i booted up the ubuntu live disk and partitioned out a 50gb space of NTFS. I even set it to boot. The same thing happens when I try to boot the XP disk.

---

### Post by Midwest-Linux on 2008-02-15
I am no rocket scientist, but I believe if you install Windows first and then Ubuntu, it may work that way. Also since you said you had Vista on the computer originally and then installed Ubuntu, maybe there are issues with that laptop trying to use XP when then laptop was only meant for Vista.

Some Acer laptops has this issue where you cannot install XP on some laptops because drivers are only made for Vista. Dell, however should NOT have that issue as they still make laptops for XP as well as Vista...but don't rely on my word for it. Funny thing is, from some of the forums I read, Ubuntu or some form of Linux can be installed on these laptops, but XP can't. 

DBan's Nuke and Boot is excellent for wiping out the hard drive, it is a free utility. I suggest use that to wipe the HD clean, then go back and try to install XP first and then Ubuntu (using the alternate text installer) and using guided partitioning to install Ubuntu. Then the Grub lets you choose between XP or Ubuntu at startup. Check with Dell first to see if XP can be installed on this laptop...it should...Note, if you originally had Ultimate or Business Vista...you should have downgrade rights to XP.

---

