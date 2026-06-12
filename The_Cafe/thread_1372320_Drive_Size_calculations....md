---
title: "Drive Size calculations..."
date: 2010-01-04
forum: The Cafe
---

### Post by Gizenshya on 2010-01-04
Don't fret, lots of people don't understand how it works.  But here in a minute those who don't will, and the knowledge can spread from there.

Anyway, drive makers measure size in individual bytes.  In other words, 1MB is one million bytes, and '1 GB' is one billion bytes.

To get that into binary size, which is what your computer measures in, it is important to remember that one binary KB is not 1000 bytes, it is 1024 bytes (since it is a multiple of 2), and each 'level' above that is 1024 of the lower level, based on this definition of KB.

So, a '10 MB' hard disk is ~10,000,000 bytes / (1024^2), which equals about 9.54 binary MB, because 1 binary MB is equal to 1024^2 bytes, or exactly 1,048,576 bytes-- not 1,000,000 bytes.

A '10 GB' hard disk is ~10,000,000,000 bytes / (1024^3), which equals about 9.31 binary GB, because 1 binary GB is equal to 1024^3 bytes, or exactly 1,073,741,824 bytes.

A '1 TB' hard disk is ~1,000,000,000,000 bytes / (1024^4), which is about .91 binary TB, because 1 binary TB is equal to 1024^4 bytes, or exactly 1,099,511,627,776 bytes.  Or, if you prefer to have 1 TB measured in binary GB, as is most common with 1TB drives, just divide it by the number we got for binary GB, or 1,073,741,824 bytes.  If we do this, we come up with 931.3 binary GB.  That number should be familiar to owners of 1 TB drives!  :)

So, just to clarify, the numbering system is **NOT random** and **NOT arbitrary**.  It is **NOT** a matter of arbitrarily subtracting x% of space, or loss due to formatting, or loss from any sort of boot record or error correction.  All the data is there, and you haven't been screwed out of anything.  If you don't take it into consideration before hand, that is your own fault.  All the data is there that was ever claimed to be.

---

### Post by blueshiftoverwatch on 2010-01-04
I know this has more to do with how much space adding a file system via a partitioning tool takes up and not how much actual usable space is on a drive. But I think that partitioning tools should do two things:

1. If I make say a 150GB Ext4 partition, tell me how much usable space that partition will take have before clicking the 'submit' button. Instead of having to wait for the drive to actually partition it's self and finding out after it's done.

2. Allow partitioning in GB and TB instead of MB, like the OpenSUSE partition tool allows you to do. I shouldn't have to keep a calculator next to my computer so I can figure out big (1GB being 1024MB, not 1000) something is. Also, this is the year 2010. How many people actually make partitions that are less than 1GB? And even if they did, such as would be the case if you wanted to setup a 100MB /boot partition. Wouldn't it be just as easy to write 0.1GB instead of 100MB?

---

