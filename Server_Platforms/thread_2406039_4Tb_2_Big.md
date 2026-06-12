---
title: "4Tb 2 Big"
date: 2018-11-14
forum: Server Platforms
---

### Post by bambamm on 2018-11-14
I went to use my 4Tb HDD but Ubuntu said the drive was too big, that I can only use up to a 2Tb drive.
How do I partition my HDD into two 2Tb drives?

The end results that I am looking for is to set all my HDDs into a RAID1 array.

---

### Post by sudodus on 2018-11-15
I guess that the problem is the partition table. The old **MSDOS partition table** can only manage 2 TB. The new **GUID partition table, GPT**, can manage more than 2 TB. I use 4 TB drives, and they work well with GPT.

You can check the partition table with the command

```
sudo parted -ls
```

and you can use **gdisk** (command line) or **gparted** (graphical user interface) to create a GPT in your drive, but please notice that all data will be destroyed, so before doing that you should **backup** all data that you want to keep.

[hr][/hr]
Edit: But I am not sure about RAID, if RAID is limited to 2 TB.

---

