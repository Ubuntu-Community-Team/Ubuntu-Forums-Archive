---
title: "External Raid Enclosure slow write"
date: 2012-08-06
forum: Server Platforms
---

### Post by Frankincense93 on 2012-08-06
Hi guys,

I noticed that when trying to backup my home PCs to my server's external RAID enclosure, it will take long than a day to even do 100GB which is stupid. I have just tried to test the hdd speeds using hdparm and dd;

The main OS HDD: 

Read:
sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   1220 MB in  2.00 seconds = 609.84 MB/sec
 Timing buffered disk reads: 274 MB in  3.01 seconds =  91.00 MB/sec

Write:
 dd if=/dev/zero of=/tmp/output bs=8k count=10k; rm -f /tmp/output10240+0 records in
10240+0 records out
83886080 bytes (84 MB) copied, 0.485983 s, 173 MB/s


External RAID enclosure:

Read:
sudo hdparm -Tt /dev/sdb

/dev/sdb:
 Timing cached reads:   1250 MB in  2.00 seconds = 625.12 MB/sec
 Timing buffered disk reads: 408 MB in  3.00 seconds = 135.84 MB/sec

[B]
Write:
dd if=/dev/zero of=/media/RAID/output bs=8k count=10k; rm -f /media/RAID/output
10240+0 records in
10240+0 records out
83886080 bytes (84 MB) copied, 5.28205 s, 15.9 MB/s
[/B]


Currently I have two 1TB Barracuda SpinPoint SATA 3Gb/s 7200RPM's in RAID 1 in the enclosure. & the Raid enclosure is a Sharkoon 5 bay RAID enclosure.



Any ideas?
Cheers,
Jack

---

### Post by Cheesemill on 2012-08-06
How is the enclosure connected to your machine?

---

### Post by Frankincense93 on 2012-08-06
It is over eSata at the moment, but It can be USB aswell.

---

### Post by rubylaser on 2012-08-06
Just with some brief Googling, it appears that your enclosure like most inexpensive RAID enclosures is processor limited.  There are a number of examples with users mentioning quick initial speeds and then seeing transfers slow down to 3 MB/s or slower over larger file transfers.  

If you can (and are willing), I'd suggest you run the disks in JBOD mode and use them in a software RAID1.  That would remove the hardware dependence and should make your sustained transfers much faster.

---

### Post by Frankincense93 on 2012-08-06
Ok, well I hope that my mobo supports port multiplying then!

Damn, now I need to setup my RAID again :( , any good links for creating a software RAID?

---

### Post by rubylaser on 2012-08-06
Sure, if you want, you can try my tutorials :)  Most are for RAID5/6, but you can substitute the raid level with **1** for RAID1 very easily.

[http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm")

---

### Post by rubylaser on 2012-08-06
Before you do that I would verify that both disks are passing SMART tests.  There are no parity calculations in RAID1, so even with an inexpensive RAID enclosure, I would have expected RAID1 to be faster than you're reporting.

But, if you want to go the software route, you can try my tutorials :)  Most are for RAID5/6, but you can substitute the raid level with raid1 very easily.

[http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm")

---

