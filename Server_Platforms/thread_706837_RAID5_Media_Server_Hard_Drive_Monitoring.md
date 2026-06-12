---
title: "RAID5 Media Server Hard Drive Monitoring"
date: 2008-02-24
forum: Server Platforms
---

### Post by Serenity55 on 2008-02-24
Hey Guys,

A few months ago I set up a media server for use in my home. I purchased one of the Dell 6 PORT CERC SATA RAID Controller Adaptec 2610SA cards that are so ubiquitous on ebay. I have 5 Seagate Barracuda 7200.10 320GB HDD's in a RAID5 configuration.

Recently I while copying a large amount of files to the server from my workstation, I heard the alarm on the server go off and the files I was copying timed out. I rebooted the server and went into the raid configuration settings and discovered that 2 of 5 drives were reported as failed. When I opened the case though I discovered that the power supply appeared to have overheated (it was a few years old.) This was confirmed when the server failed to power up at all. So I replaced the power supply with a brand new 520 watt kingwin. The server then booted and I once again entered the raid configuration to discover the drives still reported as failed. I selected the repair option and the array switched from Failed to Optimal. Everything appeared to be functioning normally and I chalked it up to a bad power supply.

Now, a day later, while again copying a large amount of files the same alarm went off and the same 2 drives reported failed. I opened the case but everything seems fine, nothing appears burned or overheated and everything smells fine. I again attempted to rebuild and everything appears to be fine again. I am very new to the server side of Linux although I have used Ubuntu on my desktop since dapper. I am very wary of just continuing on now that I have had this second failure. I have googled around for any utilities that I can use to access the SMART information past the array, but I am coming up blank. Any help at all would be greatly appreciated.

---

### Post by ttallos on 2008-02-24
Are the same 2 drives going down every time? If so try replacing them. Also it could be the controller if you have another controller card just try to replace the controller card (after getting all your data first). This sounds like a hardware problem. I have had a RAID ubuntu machine for years now. I had a simular problem with the boot sector on one of my drives it was almost undetectable for almost 2 months I had RAID5 as well. For me switching the drives to Mirror RAID1 and getting 2 new drives fixed the whole problem.

---

### Post by Serenity55 on 2008-02-24
Yes it's the same two drives. I unfortunately don't have an extra controller card to test and I'd like to try to narrow down the problem before I buy 2 new drives and a new controller.

---

### Post by astrotech226 on 2008-02-24
If you can afford the time and data reconstruction, change the order of the drives, create a new array and see what happens.  If the same two drives in different slots fail, you know what the problem is.

If the new drives in the same slots fail, you have some sort of controller or backplane issue.

---

