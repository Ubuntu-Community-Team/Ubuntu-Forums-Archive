---
title: "HD crashed, no boot, some sectors read, access secure files?"
date: 2011-06-17
forum: Security
---

### Post by Benjamin Herrington on 2011-06-17
All right, so I was running a 2-partition hard drive, Windows Vista (lamentably) on one partition, and the other running Ubuntu.  I began having trouble with the Vista partition, so I attempted to move as many of the files that I really wanted to keep as possible over to the Ubuntu partition, and then reformat and reinstall the Vista partition.  As a result, I could no longer boot to Ubuntu, and I consistently got errors back from everything that I tried on the Vista partition.

The only way that I can now access anything on the hard drive is to insert the Ubuntu install disk, go into trial mode, then mount the partition.  At long last, here is the problem:

Is there anyway to possibly make the partition bootable again so that I could burn the files to a disk?

From trial mode I can get to a number of the files on the mounted partition, HOWEVER, they are secured with the username and password of my user account on that partition.  Is there any way that I can access the files from the trial mode by entering my username/password?

Thanks in advance!
Ben

---

### Post by An Sanct on 2011-06-17
> **Benjamin Herrington said:**
> All right, so I was running a 2-partition hard drive, Windows Vista (lamentably) on one partition, and the other running Ubuntu.  I began having trouble with the Vista partition, so I attempted to move as many of the files that I really wanted to keep as possible over to the Ubuntu partition, and then reformat and reinstall the Vista partition.  As a result, I could no longer boot to Ubuntu, and I consistently got errors back from everything that I tried on the Vista partition.

The only way that I can now access anything on the hard drive is to insert the Ubuntu install disk, go into trial mode, then mount the partition.  At long last, here is the problem:

Is there anyway to possibly make the partition bootable again so that I could burn the files to a disk?

From trial mode I can get to a number of the files on the mounted partition, HOWEVER, they are secured with the username and password of my user account on that partition.  Is there any way that I can access the files from the trial mode by entering my username/password?

Thanks in advance!
Ben

Welcome to the forums!

To my understanding, files should be accessible from the "trial" mode, as you have named it (Live CD/USB test). Unless you choose to encrypt your home folder.

I think you can burn CDs/DVDs without problems from the live CD/USB (I would recommend the USB version...).

If you use a Live USB with a "persistence file", you can browse Ubuntu Software Center from there and install K3B (my favorite) or any other disk burning tool.

---

### Post by Benjamin Herrington on 2011-06-17
Thanks, you made me thing about a thing or two that I hadn't.  The files must be encrypted with the home folder because it tells me that I don't have permission to access the file(s).  Is there some sort of "log in as" option to decrypt the files?

Thanks again!

---

