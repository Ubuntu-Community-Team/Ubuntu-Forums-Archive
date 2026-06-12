---
title: "&gt;2TB fdisk partition recovery"
date: 2014-11-10
forum: Server Platforms
---

### Post by raysoft2 on 2014-11-10
Hi all,
I lost partition in ±3TB. This partition was created with fdisk (MBR). File system ext4. There is written about 2 TB of important data.
gdisk answer:
# gdisk /dev/sdbGPT fdisk (gdisk) version 0.8.1


Caution: invalid main GPT header, but valid backup; regenerating main header
from backup!


Caution! After loading partitions, the CRC doesn't check out!
Warning! Main partition table CRC mismatch! Loaded backup partition table
instead of main partition table!


Warning! One or more CRCs don't match. You should repair the disk!


Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: damaged


Found valid MBR and corrupt GPT. Which do you want to use? (Using the
GPT MAY permit recovery of GPT data.)
 1 - MBR
 2 - GPT
 3 - Create blank GPT

How to get data from disk without data lose

Thank You all

---

### Post by raysoft2 on 2014-11-10
Actually every where on web I see that is limit of MBR to 2GB, but some how I create 3TB and everything works fine. Maybe I exceed 2TB of writed data into this partition and that was reason why I lost partition table?

Any ideas how to recover data from this partition?

---

### Post by oldfred on 2014-11-10
There are some proprietary formats from hard drive mfg. to make large drives work with MBR. They may create a second partition that is some seen as another drive. Or they use non-standard sectors.

But if you forced fdisk to overwrite a gpt drive, it would have a max of a 2TiB partition.

Does testdisk in MBR mode and deeper search show files?
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)


If you use gdisk or fixparts it will either convert drive to MBR or gpt but then you probably lose any data written the other way.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

