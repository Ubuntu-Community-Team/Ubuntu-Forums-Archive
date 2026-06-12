---
title: "Partitioning for a Home Server"
date: 2010-07-15
forum: The Cafe
---

### Post by chessnerd on 2010-07-15
Alright, I'm setting up partitions for a home server. I've read various sources about partitioning for servers, but I'd like the Forum's input before I finalize it in GParted.

This server will be used mainly for local file sharing and storage. It will likely run 24/7. It might be connected to a printer, but if it is the printer won't be used much.

Specs:
1.8 GHz Pentium 4
512 MB RAM
64 MB nVidia TNT2 Pro graphics card (there is no on-board graphics)

It has 2 hard drives, a 40 GB and 80 GB. The 80 GB is newer and faster. Here is the setup I have currently:

80 GB drive:

Primary Partition -
128 MB   /boot

Logical Partitions -
5 GB     / (root)
70 GB    /home

40 GB drive:

Primary Partition -
1 GB     /swap

Logical Partitions -
5 GB     /tmp
5 GB     /var
16 GB    /usr
10 GB    (extra storage?)

Thoughts? Input? Suggestions?

---

### Post by CharlesA on 2010-07-15
Personally I would throw everything on the 40GB drive and use the 80 gig one for storage.

Then again, the way I have mine set up, I've got everything (including home and swap) on 1 hard drive and have another drive set up for data. I don't really use my home directory to store files tho.

There is really no need for a /boot partition unless your bios doesn't want to see the whole 40/80GB drive.

---

### Post by cguy on 2010-07-15
What's the (estimated) power consumption of that rig?

---

### Post by cariboo on 2010-07-15
I have a 10GB partition for / including /home. then 1TB for ripped DVD's, 750GB for recorded tv shows, 400GB for Documents, 400GB for ripped CD's, 320GB For iso's and 120GB for stuff. 

The stuff and iso's should be the other way around, as I have way to many old iso's.

---

### Post by cguy on 2010-07-15
@cariboo907: what powers your server?

I want to build one myself (file & printer sharing and video streaming for the occasional movie on the TV screen), but I'm worried about the power consumption.
More than $100/year and I consider it a waste. Is that feasable?

---

### Post by markp1989 on 2010-07-15
on my server. 

Disk1: 1.5tb
14gb for root
5gb for home 
remaining for torrents folder, where new things download to. all  my tv shows have there own folder, with the current season in the sub dir, after this season stops airing it gets moved to /media/data 

disk2: 1.5tb
all /media/data. where older downloads are kept.

---

### Post by CharlesA on 2010-07-15
> **cguy said:**
> @cariboo907: what powers your server?

I want to build one myself (file & printer sharing and video streaming for the occasional movie on the TV screen), but I'm worried about the power consumption.
More than $100/year and I consider it a waste. Is that feasable?

If you aren't doing transcoding on the fly, an Atom-based board will probably work for you.

---

### Post by markp1989 on 2010-07-15
> **CharlesA said:**
> If you aren't doing transcoding on the fly, an Atom-based board will probably work for you.

when i was doing my server , i was deciding between a atom+ion build or a zotac ion itx 9300 motherboard + e5200, i went with the zotac ion itx 9300 + e5200, as the idle power usage worked out about the same, mine uses 30w at idle. and has enough power to encode videos if needed.

edit: this is my server/htpc. [http://www.silentpcreview.com/forums/viewtopic.php?p=513174](http://www.silentpcreview.com/forums/viewtopic.php?p=513174) 

and this build uses the same motherboard i was gona use.[http://www.silentpcreview.com/forums/viewtopic.php?t=57944](http://www.silentpcreview.com/forums/viewtopic.php?t=57944)

---

### Post by lykwydchykyn on 2010-07-15
I think you're over-partitioning here.  There just aren't enough good reasons in this day and age on a home server to make separate partitions for everything.

If it were my box, I'd use about 8 GB of that 40 GB drive for /, the rest for /home, and the 80 GB drive for /srv or /home/shared or /var or wherever you like to put your shared data.

If you can't come up with a justifiable reason to partition, then don't.  It'll only bite you in the end.

---

### Post by cariboo on 2010-07-15
> **cguy said:**
> @cariboo907: what powers your server?

I want to build one myself (file & printer sharing and video streaming for the occasional movie on the TV screen), but I'm worried about the power consumption.
More than $100/year and I consider it a waste. Is that feasable?

It's a home built system:

[list]
[*] MSI G31TH-p21 Motherboard
[*] 2X1GB transcend PC5400 (667) Ram
[*] Intel E5400 Core 2 duo CPU
[*] 1TB Sata
[*] 750Gb Sata
[*] 2X400GB Sata
[*] 320GB Pata
[*] 120GB Pata
[*] Coolermaster 500W PS
[/list]

It's way over powered for what I use it for I use it for. I haven't looked at the power consumption of the system alone, as it is in my electrically heated garage/shop where there is usually at least 3 other systems running during working hours, sometimes as many as 7, plus another 2 systems in the house.

Our total power bill averages $110 per month.

---

### Post by FuturePilot on 2010-07-15
I have 2 hard drives in my server. A 20GB one which is dedicated to the system. Then I have another one 120GB that is dedicated to storage.

---

