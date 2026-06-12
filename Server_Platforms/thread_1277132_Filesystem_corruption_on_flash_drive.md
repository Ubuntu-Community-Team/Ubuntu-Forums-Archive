---
title: "Filesystem corruption on flash drive"
date: 2009-09-27
forum: Server Platforms
---

### Post by 3rdalbum on 2009-09-27
I have a home server that currently runs off a flash drive, and serves up content from a hard disk. The system is Intrepid 32-bit.

Recently when attempting to do updates, the / filesystem went read-only due to filesystem errors. I ran fsck manually twice and the problem was "fixed"; I was holding down the "y" key for a couple of minutes, there were so many errors on the disk.

Now I've got the same problem again - the filesystem has become read-only.

In future, what can I do to prevent filesystem corruption? Is it a bad idea to run a server off a flash drive, even though the main body of data is going to an HDD? Should I reboot the server every week so it can run fsck on a regular basis? Because it was a flash drive, I was using ext2; should I use a different filesystem?

Also, if I switch to running Ubuntu off an HDD, would a 2.5 inch USB HDD be fine for /, bearing in mind that it would basically be spinning all the time?

Thanks.

---

### Post by Sporkman on 2010-01-06
This is a good question. I also plan on running ubuntu server on a solid-state drive, specifically:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820167025](http://www.newegg.com/Product/Product.aspx?Item=N82E16820167025)

---

### Post by Vegan on 2010-01-06
I always suggest using a second disk and tar to make copies of data in case the root craps out.

---

### Post by mrtomservo on 2010-01-13
I'm searching for an answer to this too.  I have 3 servers running off of compact flash / ide converters.  Two corrupt like crazy, and one runs fine.  The one that runs fine is an old 600 mhz OC'ed pentium.  It's on all the time, and has been running from CF IDE for almost a year now.  I have done multiple bad sector scans with e2fsck -cfkv /dev/sdxx, and supposedly there are no bad sectors on the cards.  

The cards vary, but they are all name brand, Kingston, Sandisk, etc. I have swapped out CF IDE adaptors and they all render the same results.  I've also tried multiple filesystems.  Ext2, ext3, ext4, all end up with major file system problems.  The latest had the ext2 journals magically disappear.

It's worth noting that when I use the cards in a camera's, or for storage, the data does NOT become corrupted.

---

### Post by tgalati4 on 2010-01-22
CF cards are OK for cameras because the data is written once and spread across the flash drive in a controlled manner.  Running a server requires writing lots of small files (especially log files) and CF controllers can't cope with that.

There are industrial, IDE-ribbon flash drives, but they suffer the same problem--they break down after a while.

Unless you are running an embedded linux distro that minimizes write-backs (such as Damn Small Linux) I would expect flash drive failures.

My understanding is that the linux kernel gathers writes and sends them out in chunks when writing to a USB drive, but for a main IDE drive, the kernel treats it as a spinning hard disk--writing every sector it needs to, whenever it needs to.

Because of this behavior, you might have better luck with a USB-stick version of the server--one optimized for USB-flash use.  The kernel will certainly help extend the life of the USB stick.

I set up an old PI, 266 MHz machine with 256 MB ram (max) running DSL completely in RAM.  The advantage is that the disk would spin down, unless data was requested--serving up files, mediatomb, firefly, etc.  The machine booted off of a usb stick, but also had a CD so it could boot off of either.

---

