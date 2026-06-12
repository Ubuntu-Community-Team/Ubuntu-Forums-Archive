---
title: "Advice on home media and file server and RAID 5 compatibility"
date: 2012-07-25
forum: Server Platforms
---

### Post by cal1j on 2012-07-25
Hi,

I am relatively new to Ubuntu, and am in the process of researching my needs to build a home media center and server. I think that I am going to use some older hardware that I have laying around as a prototype system to learn and make my mistakes on before building an expensive dedicated system. The system prototype system will be built on an old shuttle box, which unfortunately only has two SATA slots. I am thinking of using aSYBA SY-PEX40008 PCI Express SATA II (3.0Gb/s) Software RAID Controller Card (on Newegg at [http://www.newegg.com/Product/Product.aspx?Item=N82E16816124027](http://www.newegg.com/Product/Product.aspx?Item=N82E16816124027)) to provide the raid capability. I have my heart set on a RAID 5 setup; the prototype system will probably only have a couple 250GB drives, and be a mockup for a system with 3+ of 2TB drives. What advice should I be  paying attention to on the choice of a RAID card? The one above that I am thinking of has built in advertised support for Red Hat Linux 8.0.9.0. SuSE Linux 8.1, 8.2. and United Linux 1.0. Is that support a good indication that it will support Ubuntu? I am planning to use Ubuntu Server 12.04 LTS as the OS with maybe LXDE as the Graphical front end (if I use a GUI at all) and virtualbox with Mythbuntu or something similar running the Media part of the system. How far off track am I? Anyone have a similar system that functions as a home file server/media center? Anyone used a cheap RAID 5 card that worked well with ubuntu?

---

### Post by blackstripes on 2012-07-25
I'm using this card:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16815124020](http://www.newegg.com/Product/Product.aspx?Item=N82E16815124020)

$20 and it has worked nicely so far.  I have a 3TB mdadm Raid 5 comprised of 4x1TB disks streaming media content for my home.

---

### Post by CharlesA on 2012-07-25
Hi,

I am using this card for the RAID array on my 12.04 file server/VM host:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16816115053](http://www.newegg.com/Product/Product.aspx?Item=N82E16816115053)

It might not be the best one out there and it is only a 3.0Gbps, but it is fairly cheap and Linux compatible.

I have been running it with regular desktop drives (3 x 2TB in RAID 5) and haven't had any problems with it.

Of course that is a hardware RAID card, and if you want to do software RAID, you can get just a cheap SATA card like the one blackstripes uses.

Charles

---

### Post by cal1j on 2012-07-25
Thanks, nice to hear that. What version of Linux are you using?

---

### Post by CharlesA on 2012-07-25
> **cal1j said:**
> Thanks, nice to hear that. What version of Linux are you using?
12.04 server x64 on my box. The drivers for the HighPoint tech card need to be built from source, but you can have it set to use DKMS to compile them when there are kernel updates, so it's not too bad.

It also worked on 10.04 server.

---

### Post by blackstripes on 2012-07-26
I'm using Ubuntu 12.04 LTS x64 as well.

---

### Post by ian dobson on 2012-07-27
Hi,

I'd have a look at using mdadm for your RAID needs. It's software RAID so it just uses the "normal" SATA ports on your motherboard.

I've been running Ubuntu/mdadm on various home servers for about the last 4-5 years without any major problems. Except for the occational hisk crash (Which RAID 5 covers nicely).

I'm currently running 8 2Tb wd drivers split into 3 RAID arrays, for backup any serving my mythTV media system.

But please don't forget RAID isn't a backup. Anything that you can't afford to loose you should backup to a seperate drive. RAID won't help you when you delete the wrong file by mistake.

Regards
Ian Dobson

---

### Post by CharlesA on 2012-07-27
The OP would still need a SATA card, cuz there is only two SATA ports on the mobo, but mdadm is a good way to go here.

Read more [here]("http://zackreed.me/articles?tag_id=22").

---

### Post by rubylaser on 2012-07-27
If the OP has an open PCI-Express x16 or x8 slot, I'd suggest an [IBM br10i]("http://www.ebay.com/itm/IBM-ServeRAID-BR10i-SAS-SATA-Controller-/280903580331?pt=US_Server_Disk_Controllers_RAID_Cards&hash=item4167287aab#ht_500wt_1209") or m1015 card (purchased off ebay) + mdadm.  This is a very flexible and cost effective way to go and would add up to 8 SATA ports to your system.  

The good news is that you really don't need expensive hardware to support even very large arrays with any of the ideas suggested.

---

