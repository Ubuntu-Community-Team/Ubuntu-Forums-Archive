---
title: "Server &quot;ata1.00&quot; Error"
date: 2009-01-05
forum: Server Platforms
---

### Post by cdnjay on 2009-01-05
Hi there folks,

Having the error below pop up a whole bunch of times when the system is doing pretty much anything. I'm on my third boot since install of the latest version of Ubuntu Server (all updates installed.) I'm running RAID 1 using a SATA controller card and I'm guessing this error has something to do with it. One of the drives is a bit older, 160 GB, the other drive is brand new as of today, 320 GB.

[ 159.987299] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 159.987383] ata1.00: BMDMA2 stat 0x686d0009
[ 159.987443] ata1.00: cmd c8/00:40:bf:c4:ae/00:00:00:00:00/e7 tag 0 dma 32768
in
[ 159.987445] res 51/04:2f:d0:c4:ae/00:00:00:00:00/e7 Emask 0x1 (devic
e error)
[ 159.987583] ata1.00: status: { DRDY ERR }
[ 159.987638] ata1.00: error: { ABRT }

The error didn't show up at all on first boot after install, a couple times on second boot and now a whole bunch on the third boot.

Any help that could be provided would be most appreciated!

Thanks,

Jason

---

