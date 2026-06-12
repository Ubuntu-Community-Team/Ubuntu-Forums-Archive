---
title: "Hardy install fails...gutsy installs perfectly!"
date: 2008-08-22
forum: Server Platforms
---

### Post by Robstarusa on 2008-08-22
So the hardy install I tried on my celeron 430 with 2 tuner cards failed badly.  It couldn't even find the CD-ROM device during the install (yet booted off the cd-rom device).

Installing Gutsy worked well.  I then upgraded to hardy.

Now the box won't start, complaining it can't find the raid arrays (1 raid1 of 2 2G cf cards, raid5 of 4 cf cards).

If I choose to boot the gutsy kernel instead, it works fine.

My suspicion is that hardy kernel defaults to setting all devices to DMA.  My cf cards & adapter do _NOT_ support any dma/udma modes, only PIO.

Any way to turn off dma in hardy?

I know PIO mode is slow, but this is a Video acquisition/transcode box.  Nothing ever touches the disks.  The box simply streams data across the network.

---

