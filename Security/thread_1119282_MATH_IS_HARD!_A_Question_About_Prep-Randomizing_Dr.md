---
title: "MATH IS HARD! A Question About Prep-Randomizing Drives"
date: 2009-04-07
forum: Security
---

### Post by Rendrago on 2009-04-07
I'm still a Linux newbie. Be gentle.

I'm writing random data to two 500GB hard drives. This is for encryption if you haven't already guessed. I'm estimating that this will take a week. This seems absolutely crazy to me. Two questions:

[B]1. How long do you think this will actually take?
2. Is there a better way of randomizing all the bits on a couple drives?[/B]

Details:
I opened two terminal windows and ran the following command in each respective window:

```
sudo dd if=/dev/urandom of=/dev/sdb
```
```
sudo dd if=/dev/urandom of=/dev/sdc
```

They're still blinking... hehe

The Box:
Release 8.10 (intrepid) 64-bit
System drive is encrypted with standard options on alternate CD.
Kernel Linux 2.6.27-11-generic
2GB RAM
AMD Athlon 64 Processor 4000+

CPU is still at 100%

```
sudo fdisk -l
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30370   243946993+  83  Linux
/dev/sda2           30371       30401      249007+   5  Extended
/dev/sda5           30371       30401      248976   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x364d515c

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f8e7a51

Disk /dev/sdc doesn't contain a valid partition table

-------------------------------------

SDB is Seagate model:
ATA ST3500630AS

SDC is Seagate model:
ATA ST3500320AS

I think one is slightly faster than the other (I'll kill the salesman that put these on the same rack if I ever see him again.)

Any ideas?

---

### Post by jdong on 2009-04-07
I'd highly recommend using a specialized tool for this such as wipe (install wipe then read its manpage's Examples section)


The problem is, /dev/urandom attempts to generate much more high-quality random numbers and the rate of random number generation will be limiting you.


For prepping a disk for encryption you don't need that good of randomization, rather I've not heard anyone say it makes a difference.

Most disks write at around 40MB/s or above, and that will guide how long it'll take wipe to process it. (should be around 20-30s per GB)

---

### Post by Rendrago on 2009-04-07
Sorry, read the man page. Thanks for the quick response. wipe is what I was looking for. Thanks again!

---

### Post by Rendrago on 2009-04-07
:popcorn:

And after a couple Ctrl+C's:

~$ sudo dd if=/dev/urandom of=/dev/sdb
^C50998610+0 records in
50998609+0 records out
26111287808 bytes (26 GB) copied, 9367.19 s, 2.8 MB/s

~$ sudo dd if=/dev/urandom of=/dev/sdc
^C41272294+0 records in
41272293+0 records out
21131414016 bytes (21 GB) copied, 7635.71 s, 2.8 MB/s

---

### Post by ibuclaw on 2009-04-07
I guess that shows how slow /dev/urandom is at generating new randomness then ;)

I agree with jdong, you never use a wrench to cut bread. :)

Regards
Iain

---

### Post by jdong on 2009-04-07
Barring Debian jokes, /dev/urandom is great when you need a high-quality seed for a crypto algorithm as it uses everything from mouse movements to incoming data packets to collect entropy, but for wiping the disk it's definitely not the right tool :D

---

