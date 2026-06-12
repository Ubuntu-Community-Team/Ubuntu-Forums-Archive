---
title: "Best FileSystem for RAID Array"
date: 2011-05-25
forum: Server Platforms
---

### Post by reebzor on 2011-05-25
So in the next few weeks I am planning on migrating my Hackintosh server to Ubuntu Server. The only reasons I installed OS X on this box was to host my Plex Media server and because HFS+ allows me to extended a partition, in the event that I add more drives to my RAID Array. The hackintosh is a real PITA and now that Plex Media Server runs on Linux, I have no real reason to stick with it.

Before OS X, I ran FreeNAS on this box, but I ultimately switched off FreeNAS becuase UFS would not allow me to extend my 4TB partition to 6TB when I added a new disk.

So my question is: Which would be the best FileSystem to format my 6TB (4x2TB drives in RAID5) array, with the intention of being able to extend the partition to 8TB (or more)?

Thanks in advance and I really look forward to using Ubuntu Server!

---

### Post by Lars Noodén on 2011-05-25
Can JFS also do that?

Then there are new ones like [Gluster](http://www.gluster.org/) and [HAMMER](http://www.dragonflybsd.org/hammer/) that I have heard and read about but not used.  They are designed to be extendable.  They would be instead of RAID and not on top of it.

---

### Post by spynappels on 2011-05-25
> **Lars Noodén said:**
> Can JFS also do that?

Then there are new ones like [Gluster](http://www.gluster.org/) and [HAMMER](http://www.dragonflybsd.org/hammer/) that I have heard and read about but not used.  They are designed to be extendable.  They would be instead of RAID and not on top of it.

I'm testing several Gluster setups at the moment, and I'm going for the belt and braces approach and RAIDing as well as mirroring the GlusterFS volumes on top.

Gluster is very easy to set up and use, but I will say that it has to run on a 64bit OS, as I had real trouble compiling from source to run on 32bit and gave that up in the end. The nice thing about Gluster is that even if you take a HDD out and plug it into another box, you can still access the data in it's original format, the Gluster system only decides where to put the data, it does not alter it in any way to live on a different filesystem or so.

---

### Post by reebzor on 2011-05-25
Thanks for your responses. I have a hardware RAID card, so I am not really interested in anything that does like a software raid.

Basically what the situation is: My array is 6TB now, if I use the RAID cards utility, I can add another 2TB drive to the array and expand it. The OS will then see the drive as 8TB but the partition will remain 6TB and the other 2TB will just be unallocated. Some filesystems will allow the partition to be extended without reformatting or losing any data on the drive. I am interested in if EXT3/4 will support this, given the size of the array. I will also be using a 64bit OS too if that matters. Thanks

---

### Post by psusi on 2011-05-25
Ext4 works just fine.

---

### Post by spynappels on 2011-05-25
Does GParted not do this with any ext3/4 file system?

---

### Post by reebzor on 2011-05-25
> **spynappels said:**
> Does GParted not do this with any ext3/4 file system?

This is basically what I am asking. When I was using FreeNAS, I had attempted to use gparted to extend the partition, but due to limitations with UFS, it would not allow me to extend a partition greater than 2TB. Is there any limitation to size with EXT3/4?

---

### Post by psusi on 2011-05-25
Ext4 can currently handle 16tb.  I believe that the kernel already has support for larger, but the utilities are still catching up.

---

### Post by reebzor on 2011-05-25
> **psusi said:**
> Ext4 can currently handle 16tb.  I believe that the kernel already has support for larger, but the utilities are still catching up.

Ugh, I guess 16TB will be fine for now.

Thanks for your help everyone!

---

