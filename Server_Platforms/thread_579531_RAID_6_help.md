---
title: "RAID 6 help"
date: 2007-10-18
forum: Server Platforms
---

### Post by c00kie1000 on 2007-10-18
So, I put some spare parts together and made myself an Ubuntu server.  The only problem is that its hard drive only has 20GB.  My temporary solution is having my 1TB external mounted on there constantly so I can always access my backed up information.  Frankly, I'm terrified that something will happen with my external, and I want to go back to just using my external as a back up that is usually off and only turned on when I update it.  

so here is what I'm working with right now:
Intel Duron processor ~1GHz (I also have a Pentium 4 ~2.7GHz lying around somewhere which I could possibly swap)
512 MB Ram (I might have a GB kit that I can add to this, but that's at home)
20GB IDE hard drive.

on my mother board I have 3 PCI slots and a PCI express X1 slot.

What raid controllers do people recommend?  Which ones are supported by Ubuntu?  Should I just get an IDE or SATA controller and do it all in software? 

I was planning on getting either 4 500GB drives or 5 320GB drives for now, and then expanding as my needs grew.   Can I still have my OS on the 20GB drive and just have the array as its own logical disk?  Or am I being a wishful thinker.

I've already read this post:
[http://ubuntuforums.org/showthread.php?t=196648&highlight=raid+6&page=2](http://ubuntuforums.org/showthread.php?t=196648&highlight=raid+6&page=2)

so please don't repeat the first page of "Why RAID 6 instead of RAID 1/0/5/1+0/0+1 etc".  

Bear in mind, with your suggestions, that I'm a college student, so my budge is <$1000 or so and that I'll probably be buying most of this stuff from newegg.

thanks for the input!

---

### Post by battyice on 2007-10-18
I have an LSI Logic SATA Raid card that runs wonderfully under linux.  They can be found resonably on ebay.

---

