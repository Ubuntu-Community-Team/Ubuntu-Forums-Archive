---
title: "External HDD read error"
date: 2008-02-26
forum: Windows
---

### Post by sayakb on 2008-02-26
Hello all
This is a peculiar problem.
I have Gutsy on my laptop. I can very well read/write on my external HDD which is in NTFS format. I do unmount it properly before removing. But when I plug it into any Windows machine, it refuses to open. Windows finds the new hardware and completes all those "rituals", I can see the icon in My Computer (though it shows Local Disk but not Glade -- which is the drive's label), but when I try to open it, it simply tells me "Windows cannot access the specified path or folder" :o

Thats weird. I thought NTFS was supposed to be read by Windows :D
Anyway, I really don't care much about the problem, but what disappoints me is that I cannot connect it to my roommate's PCs (Windows boxes) to transfer some music files.
What can I possibly do?

---

### Post by dca on 2008-02-27
If you don't care about the contents (on the externall HDD) of it then open Administrative Tools in Control Panel, select Computer Management, and then Disk Management and see if it gives an indication on the health of the file system.  If it says it's toast then attempt re-formatting right from that screen...

---

### Post by sayakb on 2008-02-28
> **dca said:**
> If you don't care about the contents (on the externall HDD) of it then open Administrative Tools in Control Panel, select Computer Management, and then Disk Management and see if it gives an indication on the health of the file system.  If it says it's toast then attempt re-formatting right from that screen...

Actually it has my 300GB of data.. I can't afford to lose it. Also, I tried disk mgmt from Vista, it simply shows that the drive is Unreadable.

---

### Post by rosegarden78 on 2008-03-24
> **LinuxIsInnovation said:**
> Hello all
This is a peculiar problem.
I have Gutsy on my laptop. I can very well read/write on my external HDD which is in NTFS format. I do unmount it properly before removing. But when I plug it into any Windows machine, it refuses to open. Windows finds the new hardware and completes all those "rituals", I can see the icon in My Computer (though it shows Local Disk but not Glade -- which is the drive's label), but when I try to open it, it simply tells me "Windows cannot access the specified path or folder" :o

Thats weird. I thought NTFS was supposed to be read by Windows :D
Anyway, I really don't care much about the problem, but what disappoints me is that I cannot connect it to my roommate's PCs (Windows boxes) to transfer some music files.
What can I possibly do?

You formatted your NTFS drive in Ubuntu/Linux which created a non-compatible boot sector and master boot record.  Your disk must contain a boot sector written by Microsoft.  For more information see this article:
[http://ubuntuforums.org/showthread.php?t=277684&page=2](http://ubuntuforums.org/showthread.php?t=277684&page=2)

Solution A:

1.  backup your drive in Ubuntu possibly to another drive.
2.  zero out your boot sector 
(dd if="/dev/sdb" of="/dev/sdc" bs=512 count=1)
3.  insert Windows CD and plugin USB drive
4.  reboot - may have to configure BIOS to boot USB first
5.  let installer delete and create a partition then reboot
6.  Plug in let Windows format in NTFS

Solution B:
0.  Backup all data
1.  Locate a USB disk with a valid MS boot sector
2.  Plug in good device first
3.  Plug in device with bad boot sector
4.  Check device letters
5.  Copy boot sector
(dd if="/dev/sdb" of="/dev/sdc" bs=512 count=1)
6.  Plug in let Windows format NTFS

Now copy data back to drive.  Any questions and more detailed instructions see the article I posted above.

Related articles:

[http://ubuntuforums.org/showthread.php?p=4578974#post4578974](http://ubuntuforums.org/showthread.php?p=4578974#post4578974)
[http://ubuntuforums.org/showthread.php?t=277684&page=2](http://ubuntuforums.org/showthread.php?t=277684&page=2)
[http://ubuntuforums.org/showthread.php?p=4579361&posted=1#post4579361](http://ubuntuforums.org/showthread.php?p=4579361&posted=1#post4579361)

---

### Post by sayakb on 2008-03-25
I would read this all.. Though I actually never formatted it under ubuntu.. :( Thanks for the links.. will check them out tonight.. :)

---

