---
title: "Binary pattern matching"
date: 2009-11-17
forum: Server Platforms
---

### Post by MMoudry on 2009-11-17
Hi All,
My disk crashed and I couldn't mount the filesystem. I was able to copy the data to another disk using : 

dd if=source ou=dest -conv=noerror,sync

All the unreadable blocks were zeroed. There wasn't that many however I would really like to find which files were affected. Is there any way under linux to scan for a certain binary pattern inside files? In this case it would be continuous blocks of zeros.

MM

---

### Post by Vegan on 2009-11-17
Sorry to hear your disk died. Sounds like a major failure.

dd is not that sophisticated. You are best to pick through the wreckage and save what you can. Then trash the disk.

IF you want to scan the sectors, that would require some programming.

---

### Post by MMoudry on 2009-11-17
I am sorry I haven't expressed myself correctly :

I was able to recover a working filesystem with nearly all the data intact. During the copy with dd however there were a few sectors that were unreadable from the original disk, I have configured dd to fill the unreadable space (on the new disk) with zeros.

ie. I got this from the process :
(Original Disk)  DATADATADATADATADATADATADATADATADATADATADATADATA
(New Disk __)  DATADATADATA0000000ADATADATA000000TADATADATADATA

Basically dd created a few zero filled holes in the data where it was unable to read from the original disk. Now my problem is that I would like to detect in which files are those holes located. ie... scan the filesystem and give me a list of files in which the patern exists '0000000000000000000000000000000000000000000000000000000'

Is there any unix command to do this?

I imagine it would be equivalent of doing :
1. Locating the pattern in question in the raw filesystem.
2. When pattern found find it's start and end sector.
3. Read the filesystem information to see which files or parts of them were written between the start and end sector of the pattern match.

Thanks,

MM

---

