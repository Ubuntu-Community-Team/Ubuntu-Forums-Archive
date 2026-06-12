---
title: "updated hard disk survival"
date: 2015-03-14
forum: Server Platforms
---

### Post by Vegan on 2015-03-14
I have updated my page on [hard disk survival]("http://hardcore-games.azurewebsites.net/wp/hw/hd/harddisk-survival.php"), more disks and moved it to Azure where it is safe :KS

bought a SATA dock, internal and it allows me to plug a disk into a slot on the front panel to copy files back and forth

any way to get linux server to support hot plug SATA insert for backups etc, and call a backup script etc?

i have 4 available 2.5" disks that I can run 2 at once with the 2 slots, and I can also use 3.5" disks too

then a disk in a stationary cabinet is safer than being online vs miscreants

---

### Post by TheFu on 2015-03-14
My eSATA dock does hot-plug no issue, but cheaper eSATA cards don't. There is a specification required that many of the cheaper eSATA chipsets don't seem to have. 

Seeing when a partition gets mounted isn't hard. Simple scripting - or perhaps just have a udev rule?

I'm confused what this has to do with azure. It isn't like you can walk into any of those data centers, get onto the floor where your VM is running and connect a eSATA dock to it.

---

