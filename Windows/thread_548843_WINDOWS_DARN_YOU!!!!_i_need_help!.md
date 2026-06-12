---
title: "WINDOWS DARN YOU!!!! i need help!"
date: 2007-09-11
forum: Windows
---

### Post by taehC on 2007-09-11
Hey i need help...
So i just noticed i was very low on partition space for windows and i needed to repartition my drive.  so i put in the gparted live cd and repartitioned my drive.  it worked fine until... i tryed to reboot into windows...  now whenever i boot into windows it goes until it gets to the login screen but only shows the logo...
i have tried to do safe mode, tryed the last working settings, tryed basically everything.  i tryed to do the cd repair thing but when it asked for my password i typed it in and it didnt accept it, i also tryed my username and my name... nothing worked...
PLZ SOMEONE HELP!!!

---

### Post by karellen on 2007-09-12
if you have windows installation disk, pop it it and boot. then select from the installer something like repair a previous windows installation...
I hope you didn't erase your windows partition or something like this and that's just an mbr problem

---

### Post by Bungo Pony on 2007-09-12
Yeah, I messed mine up a couple of times like this. I seem to recall reading somewhere that you need to defrag the Windows partition before resizing it.

---

### Post by darksong on 2007-09-12
If you were very low on space and deiced to partition your Disk you sir are a fool. You still need space for partitioning your 80gig hd (with 79gigs used) does not give you x2 80gig partitions, it will give you partition 1 with X space and partition 2 with X space and by the sounds of it you have partitioned your hardrive so it does not have enough space to store all its files. The same would happen in linux, mac ect - its not a windows problem.

If you did have enough space for your partition (you still need about 2 gigs free in the windows partition for it to function) then i am sorry for calling you a fool.

---

### Post by taehC on 2007-09-12
i know what i did
i moved the start of the windows partition and now windows has no clue how to  boot...

---

### Post by karellen on 2007-09-13
> **taehC said:**
> i know what i did
i moved the start of the windows partition and now windows has no clue how to  boot...

you need a windows installation disk to restore your mbr

---

### Post by PSolutions on 2007-09-28
Hi, 
Download a live boot cd, somthin,g like hirrens bootcd and there yuo can repair the mbr without a problem.

---

