---
title: "Server install partitioning"
date: 2011-11-28
forum: Server Platforms
---

### Post by northernerchris on 2011-11-28
Hi,

Basically I'm trying to setup an Ubuntu web Server (10.04) as follows:

Drive 1 (160Gb) = sda / (152Gb set as bootable) and swap (8Gb as 4Gb of memory) partitions ext4
Drive 2 (500Gb) = sdb (500Gb) partition and set to be used with RAID
Drive 3 (500Gb) = sdc (500Gb) partition and set to be used with RAID

RAID 0 set to use sdb and sdc and mount /var partition

Once the install has completed and it reboots all I get is a black screen with a blinking cursor, no attempt to boot.

If I take the 160Gb drive out of the equation and do a simple partition scheme of / and swap partitions it boots fine.

Am I being awkward or just missing something simple? I just thought doing it this way would give me as much space available 1Tb, be quick and by using a separate drive to boot off if anything goes wrong the system side of things at least the web site info would separate and safe.

Is there a better way to do this?

Thanks in advance for any help,
Chris

---

