---
title: "Riddle me this..."
date: 2007-07-13
forum: The Cafe
---

### Post by Roasted on 2007-07-13
2GB MicroSD card.

It came formatted in the FAT16 file system.

Linux reads it as...

1.9GB total
132 songs on it = 750MB used
1.2GB remaining

Yet when I add anything more to it, such as a 4.0MB song file, it says no available space. Yet... IT SAYS 1.2GB REMAINING!! 

Even my phone (Motorola KRZR) says it can't transfer anything else. It says 1.2GB free, yet when I try to transfer a file from my phone to my memory card it says unable to move.

Whyyyyyyyyyy

---

### Post by ThrobbingBrain66 on 2007-07-13
What happens if you back up all the data currently on the card and reformat it to fat32?

---

### Post by smoker on 2007-07-13
i had a 128MB flash drive once, that somehow got fubar'd, and stated every file on it was 4GB in size! a reformat fixed it for a while, but i incorrectly removed it in a windows machine and think that was the ultimate cause.

if you can, backup the data and try a reformat.

---

### Post by Roasted on 2007-07-13
I can't format it to FAT32 from within linux, can I?

---

### Post by tszanon on 2007-07-13
I don't really remember, but it's caused by FAT16. Another example of this problem: ever tried to store icon files in a floppy disk? Each file is less than 1KiB, but you can't store more then about 700 icons. There's nothing you can do to solve this, but reformatting it to anything but FAT16.
> **Roasted said:**
> I can't format it to FAT32 from within linux, can I?
Yes, you can. Use the Floppy Disk Formatter (or whatever it's called) under...Accessories? Oh well, memory is starting to fail...
If I recall correctly, you'll see something called vfat, not FAT32.

---

### Post by yabbadabbadont on 2007-07-13
> **Roasted said:**
> I can't format it to FAT32 from within linux, can I?
Yes you can.  As an example:
```
mkdosfs -F 32 /dev/xxxx
```
Replace the "xxxx" with the correct partition device.  In my case it would be /dev/sdb1, but you need to use the correct device for your system.

---

