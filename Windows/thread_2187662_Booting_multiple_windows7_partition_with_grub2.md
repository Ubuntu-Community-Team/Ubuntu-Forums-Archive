---
title: "Booting multiple windows7 partition with grub2"
date: 2013-11-13
forum: Windows
---

### Post by mats.genfors on 2013-11-13
Hi,

My goal is to try and clone a working windows7 partition and be able to boot each copy from the same disk. I need to hide the windows installations from each other as well and each copy must boot as C:.

What i've done so far is to install linux server 12.04 on the first primary partition. The 2 windows7 clones are on primary partiton 2 and 3. I created 2 windows entries in grub and used the parttool to hide the windows installations from each other. This almost worked, the first clone on partition 2 boots fine without seeing number 2 but I'm having trouble booting number 2, it starts as far as displaying a windows logo but then it froze. I suspect I need to modify my second clone of windows in some way. Tried changing the UUID but that did not help. 

Has anyone tried to do this?

--Mats

---

### Post by oldfred on 2013-11-13
Moved to other OS.
Not sure if Windows offically allows that or not?

       To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

Windows also has internal info like UUIDs in BCD. And each NTFS PBR has the start & size of the partition that must match the partition table. So minimum will be to run chkdsk from Windows to update PBR and edit BCD.

---

