---
title: "Commputer boots to grub rescue after deleting linux partritions."
date: 2015-06-08
forum: Windows
---

### Post by peter197 on 2015-06-08
I had linux mint and windows 7 dual booted. I deleted the linux mint partritions like an idiot and now when i try to boot it says
Error: unknown filesystem.
Entering rescue mode...
grub rescue>
I tried boot-repair to fix it but the automatic repair didnt seem to change anything       [http://paste.ubuntu.com/11653992/](http://paste.ubuntu.com/11653992/)
I also tried to fix it with a windows 7 cd but i just got stuck here (attachment) and i dont know how to load drivers.
I just want to be able to use windows without loosing all the data that i have.

[COLOR=#000000]Finally i fixed it! I removed all my hard drives but the main one then reinstalled linux mint. Then the windows 7 installation cd was able to repair it somehow and now it boots up fine![/COLOR]

---

### Post by howefield on 2015-06-08
Thread moved to the "*Windows*" forum.

---

### Post by yancek on 2015-06-08
You have three hard drives all of which have windows operating systems or partitions.  You have Grub in the mbr of the second (500GB) drive pointing to what I suppose was your Mint partition (sdb5) but which is now formatted ntfs.  What happens when you try to boot either of the other drives?  Can you boot the smaller xp drive?  Do you have a windows 7 installation disk?  Recovery CD with a Repair option?

---

### Post by peter197 on 2015-06-08
I have the win 7 installation disk and tried the repair option  "[COLOR=#000000]I also tried to fix it with a windows 7 cd but i just got stuck here (attachment) and i dont know how to load drivers."
The smaller drive doesnt have any os on it its just an old drive i was using to store games on. same with the 120 gb ssd. that ones new. I ran some commands that i found online from linux mint running on a cd and it changed grub back to windows boot manager. But the windows boot manager wont start. it says the boot selection failed because a required device is inaccessible. I am assuming that reinstalling linux mint will fix everything so im about to do that.[/COLOR]

---

### Post by peter197 on 2015-06-08
Finally i fixed it! I removed all my hard drives but the main one then reinstalled linux mint. Then the windows 7 installation cd was able to repair it somehow and now it boots up fine!

---

