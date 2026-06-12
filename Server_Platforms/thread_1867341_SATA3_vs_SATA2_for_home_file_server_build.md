---
title: "SATA3 vs SATA2 for home file server build?"
date: 2011-10-22
forum: Server Platforms
---

### Post by darkod on 2011-10-22
Hello all.
This is not strictly Ubuntu question but since I am active here I thought I could receive some advice. Also, wasn't sure whether to post in the Server, Hardware or Networking sections, so I hope I'm on the right place.

I am preparing to build for myself an Ubuntu home file server. Nothing fancy, mini-ITX board with built-in dual core Atom D525, 2GB DDR3 and two HDDs in software RAID1.

Now comes my dilemma. Since SATA3 disks are more common on the market now, and it seems even cheaper than SATA2, I will probably get Samsung F3 SATA3 disks instead of the SATA2 I was planning. But the board has only SATA2 ports (4 of them). Is it worth spending more for board with SATA3, or for a SATA3 adapter?

If I understand it right, mechanical disks can not even fill out the SATA2 bandwidth, let alone SATA3. So, is spending and planning for SATA3 just a waste of time and money? Will there be any real life improvement?

If it matters, the server will be in a wired 1Gb network.
Also, if you need more info, the board I am planning is the Gigabyte D525T-UD.

Thanks in advance for any advice.
Darko.

---

### Post by rsvancara on 2011-10-23
Here is something to consider:

Your 1Gb/s network interface will most likely be your bottleneck.  here is why.  1Gb/s interface transmits data at roughly 100MB/s after overhead.  

SATA disks performance is not that great (in comparison to technologies like SSD) and depending on your workload for your file storage, two SATA disks MAY saturate the Gigabit interface in a purely sequential I/O situation, but if you are in a random I/O situation (accessing many files at once) your storage will slow down considerably.  

So in a nutshell, I do not think it really makes a difference for your setup.  SATA3 may be more mainstream and actually cheaper than SATA2.  

Also you may want to speed up your purchase.  Western Digital's plants just flooded and a hard drive shortage is expected...at least according to Slashdot.

---

### Post by darkod on 2011-10-23
I am even more confused now.

1. Even though the SATA2 is specified as 3Gb/s and SATA3 at 6Gb/s, in real life random access it never gets even close. I thought the disk will be the bottleneck, not the network interface.

2. Having two disks in my case does not improve the transfer rate because I will not be running them in RAID0, but in RAID1. RAID0 does in theory double the transfer rate but not RAID1.

---

