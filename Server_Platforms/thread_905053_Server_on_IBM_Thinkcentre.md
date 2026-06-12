---
title: "Server on IBM Thinkcentre"
date: 2008-08-29
forum: Server Platforms
---

### Post by jay3712 on 2008-08-29
I am thinking about getting an IBM Thinkcentre M50 or S50 for about $175. It's a P4 2.8, 512MB, 40GB, CD-ROM. Here is what I want to do with it:
1. File server which I can access from any computer, mostly for documents from school computers.
2. Print server
3. Creating backups of my 2 other computers (1 XP, 1 Ubuntu), school papers mostly.

Mainly I want to know if this is going to be a good hardware setup for me. I can get gigabit ethernet for a bit more. Would this be worth it?

I don't have any Ubuntu Server experience yet, but have been reading a lot in the last couple days. Hopefully someone can point me in the right direction. 

Thanks,
Jason

---

### Post by cariboo on 2008-08-30
I would install a larger hard drive, and don't bother with the gigabit nic as you won't be able to use it any way if you are going to remotely access your server. Otherwise you can run a server on almost any pc hardware. I'm running an Athlon 64 1Ghz with 512MB ram, 1 120GB ATA HDD and 2 400GB SATA HDD in a raid1 array, it serves my needs perfectly. So this hardware should work well for you.

Jim

---

### Post by windependence on 2008-08-30
I have two of these in production although they run OpenSuSE. They are good machines and IBM's support is great if you need it.

As for the GigE, yes Cariboo, he would be able to use it internally. It will greatly speed up his file transfers over his LAN. Doesn't do much good for WAN, but for backing up files and the things he said he was going to do, I would recommend it. 10/100 cards are almost obsolete, and GigE is just as cheap. You can get cards for $10.

-Tim

---

### Post by mellowd on 2008-09-01
A gig card will be of no use unless you have a gig switch.

If your other pc's are also running at 100mbps then there is no real point unless all of them are going to be mass copying at the exact same time

---

