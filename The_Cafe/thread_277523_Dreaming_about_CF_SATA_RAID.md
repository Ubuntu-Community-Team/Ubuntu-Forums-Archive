---
title: "Dreaming about CF SATA RAID"
date: 2006-10-14
forum: The Cafe
---

### Post by Peepsalot on 2006-10-14
I just read this article about a 32GB solid state flash hard drive from Samsung.
[http://www.tomshardware.com/2006/09/20/conventional_hard_drive_obsoletism/](http://www.tomshardware.com/2006/09/20/conventional_hard_drive_obsoletism/)
It sounds like a very cool product.  However, I think the prices are a bit steep at the moment.  [http://www.dvnation.com/nand-flash-ssd.html](http://www.dvnation.com/nand-flash-ssd.html)

So I came to the idea of building a SATA RAID array using some hardware raid controller, and these:
[SATA Compact Flash adapter](http://www.tomshardware.com/2005/08/18/accelerated_compact_flash/)
Can be had for $34.50ea directly from [addonics](http://www.shopaddonics.com/itemdesc.asp?CartId={BCBFD56D-0ED9-4470-8293-76505AEVEREST09B3CE}&ic=ADSACFB)

Here are some perceived advantages/disadvantages off the top of my head
_Advantages:_
Upgradeable/Replaceable cards
Might be done for less $/GB ?
Possible better performance than Samsung drive?
_Disadvantages:_
Probably no way to do in a laptop, desktop only
All the reliability of RAID 0 coupled with limited flash writes ;)

_Some things to consider:_
What are currently the fastest available CF cards?
Which cards would be the best balance of speed/capacity/value to fill the array with?
How crazy do you want to go with the RAID? 2,4,6,8 channel?
What SATA RAID controllers are supported in Linux and what would they cost?
The end product should at least perform better than a single "moving parts" hard drive.

I think it would be a fun project, what do you think?
I'm probably  not going to be building this any time soon due to fundage, but in the somewhat near future when I can scrounge together some bills I think I would like to try it.

---

### Post by Kateikyoushi on 2006-10-14
I have been waiting for a long time for those flash drives, last spring they promised september, and look were are we now.

Anyway the samsung writes those chips same time so you won't be able to match the performance unless you make the raid with 4 drives maybe more, currently the interface limits the performance.

The price of flash drops about 40% each year and last month they announced 40nm chips which doubles the density. I wonder how it translates to performance, was easier to predict with hdds.
Next year we can get cheaper 32GB or bigger 64Gb flash drives.

---

### Post by Peepsalot on 2006-10-17
mmmmm, 40mb/s transfer rates *drool*
[http://www.sandisk.com/Products/Catalog(1189)-SanDisk_Extreme_IV_CompactFlash.aspx](http://www.sandisk.com/Products/Catalog(1189)-SanDisk_Extreme_IV_CompactFlash.aspx)
I guess that by itself could possibly beat many existing hard drives.

But I still want it with RAID!  Just think, combine 4 of them for ~160mb/s

---

### Post by Kateikyoushi on 2006-10-17
That's 2240$ just for the flas cards, and you won't reach 160MB/s with it not mentioning how often could you use it, in that price range a scsi raid can be also considered.

The SSD's biggest advantage performance wise would be it's seek time, at least for most of us.

---

