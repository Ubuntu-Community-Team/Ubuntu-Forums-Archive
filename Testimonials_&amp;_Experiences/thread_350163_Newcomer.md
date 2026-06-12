---
title: "Newcomer"
date: 2007-01-31
forum: Testimonials &amp; Experiences
---

### Post by Pugwash on 2007-01-31
Hi everybody,

I just installed ubuntu on my dell laptop a couple of days ago and so far I've been very impressed, I can't believe I didn't try it earlier. I'm also very surprised that the installation process was so smooth, didn't encounter any major problems ( I was certain I was just trashing my computer). I won't deny that it seemed quite alien at first (compared to windows), and I'm still getting the hang of it (especially working the terminal) but there's so much resources on the net to help linux-illiterates like me (this forum was a great help). The only thing I regret is that is that I only dedicated 10 % of my hard drive (on a 120gb hard drive) for the ubuntu partition, the rest for windows xp (yeah I'm dual booting, shame on me). Is there any way to easily resize the partitions?  Anyway thanks to all the ubuntu developers and to the people involved in the running of this forum.

Cheers

---

### Post by hal10000 on 2007-01-31
To answer your question we need to know your partition table. Open a terminal window and post the output of [COLOR="Red"]sudo fdisk -l[/COLOR]
You can mark the output with your mouse and simply paste it with the middle mouse button into your browser/editor.

---

### Post by Pugwash on 2007-01-31
Hi, 

Thanks for the reply. Here's the results:

> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2   *          12       12096    97072762+   7  HPFS/NTFS
/dev/sda3           12097       13987    15189457+   f  W95 Ext'd (LBA)
/dev/sda4           13988       14593     4867695   db  CP/M / CTOS / ...
/dev/sda5           13727       13987     2096451   dd  Unknown
/dev/sda6   *       12097       13655    12522604+  83  Linux
/dev/sda7           13656       13726      570276   82  Linux swap / Solaris

Partition table entries are not in disk order




---

### Post by vigleik on 2007-01-31
Depending on your partition table, you might or might not be able to do the following: Shrink windows more, and then create another partition to keep your data on. Resizing the linux partition(s) is hard, so it's better to just make another partition. Of course, if you used up your quota of 4 primary partitions then things are more difficult....

---

### Post by Pugwash on 2007-01-31
Ah, ok. I think I'll leave it then for a while till I get a bit more accustomed.

---

### Post by homh on 2007-01-31
You might consider reintstalling Ubuntu with the partiion sizes you want as being easier.

I had about 200 gb of free space on my hard drive and gave half to Ubuntu and now think I should have given more as I dont really use Windows.  Its just there in case I need it for something.  But its good for now.  That is plenty os space for my current needs.

---

