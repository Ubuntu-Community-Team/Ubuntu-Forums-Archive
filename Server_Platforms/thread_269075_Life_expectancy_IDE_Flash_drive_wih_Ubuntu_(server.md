---
title: "Life expectancy IDE Flash drive wih Ubuntu (server)?"
date: 2006-10-01
forum: Server Platforms
---

### Post by Swiss2K on 2006-10-01
Hello,

I like to install ubuntu on a IDE flash drive like this one: [http://www.transcend.com.tw/Products/ModDetail.asp?ModNo=26&LangNo=1](http://www.transcend.com.tw/Products/ModDetail.asp?ModNo=26&LangNo=1)

I have concerns about the life expectancy of these drives since they last only about 10.000 read/write cycles. This doesn't sound like a lot to me, but on the other hand I have no idea how intensively Ubuntu writes to the disk in normal 24/7 operation as webserver.

anyone any experience with this?


ps. I've read about distro's with read-only filessystems but that's no option because I must be able to write to the disk.

---

### Post by CyberX on 2006-10-01
Hi,
It mostly depends on the load your web server will have.

I built a home web server just for testing purposes, so I used a (very old) PC I had around, and used a 512 MB Sandisk Compact Flash  with a CF-IDE adapter. Sandisk says this CF card stands at least 300 000 cycles (the new models stand perhaps 10x more, and they are also faster), but I don't know exactly how to convert that number to hours. What I do know is this server has been working 24/7 in the last month, totally silent (no moving parts at all).

I guess that if you have lots of memory to prevent swapping and configure your server with just the minimal services, you might use a CF card for a year in a home server... if you don't get slashdotted :-D

---

### Post by McLogic on 2008-05-07
I'm interested in this to try and make software RAID work as easy as the RAID on the Infrant (now Netgear) ReadyNAS products. These products are Samba/NFS/FTP/RSYNC/webDAV, DHCP, and print servers that feature disk-failure-resistant storage. The downside is that they are slow and expensive.

The X-RAID  appears to be just standard software RAID-5 (ext3 + lvm2 + md + mdadm) and some scripts to start RAID rebuilds. This makes it easy, just put drives in and the array expands or rebuilds. If the OS is on the flash memory, it is less likely to fail, and so the system will boot and run the detection/rebuilding scripts.

[http://www.readynas.com/?cat=4](http://www.readynas.com/?cat=4)

This means the RAID maintenance can be done by just the physical act of attaching drives. So if a drive fails while I'm on a 2-week business trip, someone else in the family can replace the drive. I think we all want the largest capacity that also lets one drive fail without data loss (AKA RAID-5).

I bet this can be done with a 2GB flash IDE device (about $30). This can be done with the devices above from Trancend or with CF and SDHC to IDE converters. They cost about $10 to $35 (USD) depending on source, speed and aesthetics. It may even be possible with a $10 2GB USB flash drive, but many of them are super-slow.

For cheap, try newegg.com and for nice try addonics.com .
[http://www.addonics.com/products/flash_memory_reader/adidesd.asp](http://www.addonics.com/products/flash_memory_reader/adidesd.asp)

Does anyone have any idea if this would work?

If it does, then :guitar:

---

