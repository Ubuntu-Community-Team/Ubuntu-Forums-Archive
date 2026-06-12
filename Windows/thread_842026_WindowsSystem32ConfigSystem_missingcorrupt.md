---
title: "/Windows/System32/Config/System missing/corrupt"
date: 2008-06-27
forum: Windows
---

### Post by AdrianStrays on 2008-06-27
I'm going to ask here rather than a Windows forum because I think Ubuntu users are a little more creative/competent at handling computer issues than Windows users are.


Any way, I booted my family's Vista/Ubuntu computer and received a system error when attempting to start Vista.  I was told that System.exe was either missing or corrupt.  Simple enough, I load Ubuntu, force mount the drive and edit the System.sav to System.exe.  It still doesn't boot.  After Googling around, it seems the only way to fix this issue is through the Windows Recovery Disk, however like the vast majority of users, I did not receive a disk, I received a recovery partition.  After attempting to load by pressing F11 at start up, I was brought to the GRUB Menu.  The recovery partition is there.  My theory is the addition of the Ubuntu Partition some how prevents the bootloader from recognizing the Recovery Partition.  How do I fix this, or alternative, how do I fix the issue without having to use the recovery partition?

---

### Post by joezamboni on 2008-06-27
Try copying some of the windows files from a different vista computer. If that doesn't work, wipe the windows partition and start again.

---

### Post by fiddledd on 2008-06-27
Firstly, it's normally F8 to boot from the Recovery Partition. However if it doesn't work here's s Vista Recovery CD:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

