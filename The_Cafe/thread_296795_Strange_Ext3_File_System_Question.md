---
title: "Strange Ext3 File System Question"
date: 2006-11-10
forum: The Cafe
---

### Post by Reiko on 2006-11-10
At the university we study the Unix File System, designed by Ken Thompson.I learned that a file has his own inode(exclude the hard links), which is different to the inode of the other files. So the question is: Why if i type "ls -i /" /proc and /sys got the same inode "1"(one). I use Ubuntu 6.10 Edgy, and the ext3 File System.

---

### Post by 23meg on 2006-11-10
Things in /proc and /sys aren't files per se, thus the inodes aren't EXT3-specific; they're so called pseudo-files, the kernel's filesystem interfaces which point to things happening all over the system.

---

### Post by po0f on 2006-11-10
Reiko,

/proc and /sys aren't ext3 filesystems.

[/proc filesystem](http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/ref-guide/ch-proc.html).

Sorry, can't find one for /sys, but it is supposed to represent the current state of the kernel.

[EDIT]

So slow...

---

### Post by Reiko on 2006-11-10
thank you guys :)  , now after reading that i understand

---

