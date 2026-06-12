---
title: "Faster MySQLDatabase"
date: 2011-04-16
forum: Server Platforms
---

### Post by Vegan on 2011-04-16
Given the way most databases work, SSD disks seem to make sense.

So using one machine with a SSD and use only MySQL setup as a server.

Its easy to change MySQL to listen to the LAN.

We sites often are rotting away as well but they are sequential in nature so using a hard disk makes better sense.

One idea is to use a secondary SSD and then simply link to it under the default MySQL directory.

---

### Post by rubylaser on 2011-04-16
I have no idea if you're asking a question or making a statement.  One hard drive whether SSD or spinning disk is never the way to go it you want fault tolerance (or speed for that matter).  A RAID array makes sense with MySQL and in high performance environments splitting across multiple arrays makes more sense.  So, multiple SSDs in a RAID array or something like the Fusion-IO or upcoming Sandforce based PCI-e cards are the way to go if you want absolute speed. But, in most cases a nice RAID10 array with 15K RPM SAS drives is more than adequate for high performance.

Here's the Fusion-io Duo, it's not a cheap part.
[http://www.fusionio.com/products/iodriveduo/]("http://www.fusionio.com/products/iodriveduo/")

---

### Post by elico on 2011-04-17
in any case of not very large databases one ssd driver will give more performance then what you probably need.
if it's a large DB that need "redundancy" you can consider it... but still most of the ssd drive size VS price then you better use a raid 5 fo sata or sas to use as a backup DB.

---

