---
title: "How best to use RAID &amp; LVM?"
date: 2010-11-24
forum: Server Platforms
---

### Post by molinus on 2010-11-24
I'm hoping someone can post info or a link that illustrates how best to use RAID & LVM in creating a fileserver and internal webserver.

I have installed Ubuntu 10.04. :D

I have 2 RAID mirrored sets:
RAID#1 = 2 - 600 GB drives - 3 partitions
1	/boot	256MB
2	/		320GB
3	/home	280GB

RAID#2 = 2 - 1 TB drives - 1 partition (currently)

I have 2 Hot Swap drives for offsite backup:
1 - 1 TB hot swap drive - 1 partition (currently)
1 - 2 TB hot swap drive - 1 partition (currently)

My goals:
Run an internal ERP website, test websites for design, accounting,  production, customer files, invoice files, purchase orders, warehouse documents, shipping documents, and backups, among other things.

Should I make several partitions on RAID#2 and make an LVM group with separate volumes for "Accounting", "Production", etc. ?
If so, do I create directories and mount them as /accounting, /production, etc. ?

Is there a better way?

Any help at all is much appreciated.

---

