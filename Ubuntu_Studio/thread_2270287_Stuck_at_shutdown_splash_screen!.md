---
title: "Stuck at shutdown splash screen!"
date: 2015-03-21
forum: Ubuntu Studio
---

### Post by anthonyjeswald on 2015-03-21
Hi, everyone. So, I have a Lenovo Z570 running Ubuntu Studio 14.04, and  for some reason it freezes when shutting down. I have seen other threads  on this issue, but none of the fixes have worked for me:

1. shutdown -h now brings me to the shutdown splash screen, just like  doing a shutdown from the normal dropdown menu method. It freezes at the  splash screen.
2. I tried editing /etc/default/grub file to reflect the following:  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force" which didn't work. 

Thanks for your help!

---

### Post by marseille2 on 2015-03-23
There's some bugs on launchpad about this, but I still can't find a good answer to this huge question.

I endured this problem on two computers both with Ubuntu 14.04 installed. The older of the two still has to do a hard shut down every single time, so I'm going to install either an older or lighter version of Ubuntu on it. 

But with this one, I first unmount all external drives, then log-out of my account. After logging-out, I do a full shut-down. And with the most recent kernel installed (and upgrading to the new systemd), I'm actually able to reboot... before that something seemed to be clashing with UEFI (note that the old computer has good old regular bios, so it just wants to reboot instead of shut-down).

So although this is not much help -- if you find a fix, please share! -- ... if you have UEFI, try to read up on how it works with Ubuntu before messing around with ACPI too much. I would also file a launchpad bug, and probably look through the security and hardware forums as well.

---

