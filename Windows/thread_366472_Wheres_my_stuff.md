---
title: "Wheres my stuff???"
date: 2007-02-20
forum: Windows
---

### Post by Entity` on 2007-02-20
I recently reinstalled WinXP on my server and when I plugged in my drives; guess what happened?  I have 3 (1-20,1-30, and a 60GB) other drives on my system and everything on the 20 mysteriously disappeared from physical view.  What I mean by that is that Everything is there, its just that I cant see it or access it.  Disk defragmenter shows that its still there, and so does the disk properties, but I have no means of getting to it at all.  The disk is fully functional and nothing is broken; and I have not written anything to it at all since it happened.

So if there is anyone out there who can offer assistance, I kindly ask that you please help me.  Thanks in advance everyone.

](*,)

---

### Post by JoeFontana on 2007-02-20
Try viewing the contents from a command prompt.

Open cmd.exe, CD to the drive in question and dir.

This should show your data in case something in Windows Explorer stuffed up and screwed with how it views your files.

---

### Post by erlyrisa on 2007-02-21
there is supposed tobe some sort of way to specify drive letter assigning. It's in administrative task of the control panel.

(xp likes to assign it's drive letter as the last one above other bootable partitions/devices)


eg. on my computer where there was win98 on c: and i have a second drive for data as d: , xp once installed calls itself E: which is actually c: for a normal dos boot.

---

### Post by Entity` on 2007-02-21
I can see my drive, it is mounted and functioning properly.  My boot/system drive is C:/ like it should be, and the drive in question is E:/

Im thinking about deleting the partition, reformatting and then using ZAR (Zero Assumption Recovery) to get it back.  ZAR works just fine for me, it just takes some time (anywhere from 30min to almost 3 hours).

Of course my new partition would be FAT32 so I could mount the drive in Linux as well.:mrgreen:

---

