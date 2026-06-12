---
title: "Removing Windows Xp from system"
date: 2010-12-05
forum: Server Platforms
---

### Post by teekay13 on 2010-12-05
I have just recently installed Ubuntu Server 10.10 32-bit onto an old Gateway Solo 5300 laptop to run as a test server. Since I want it to use all of the disk space, how do I remove the other OS and its existing programs.
Thanks,
Tom

---

### Post by CharlesA on 2010-12-05
You should have been able to select "use full disk" during install.

Otherwise, it's possible to boot something like gparted and delete the Windows partition and extend the partition Ubuntu is installed on, but that's risky and I wouldn't suggest it unless you have a good working backup.

---

### Post by sikander3786 on 2010-12-05
Delete the Windows partition and run *sudo update-grub* to get rid of Windows entry in Grub menu.

Regarding resizing of root partition, it is not recommended in most cases. Instead I'd recommend to create a new partition in the freed up space, mount it under Ubuntu as a separate partition and use it for whatever you want to.

If you still want to go for resizing, this might help.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

