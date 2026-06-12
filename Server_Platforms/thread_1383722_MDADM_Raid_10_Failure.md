---
title: "MDADM: Raid 10 Failure"
date: 2010-01-17
forum: Server Platforms
---

### Post by ronin8600 on 2010-01-17
I have 4x1TB Samsung SAMSUNG F1 RAID Class HE103UJ 1TB drives in a raid 10 array and one of my drives have recently showed up as failed in the array.

After some investigation it appears it was dropped because of reallocation events, but the reallocated sectors seem to be within the threshold.

Reallocated Sector Ct: 235
Reallocated_Sector_Ct 0x0033 095 095 010 Pre-fail Always - 235

I've added the drive back to the array and seems to be working well, I've run hdparm benchmarks and performance appears to be the same.

Should I send the drive back in for replacement?  Is this a sign that the drive will soon fail? It seems to be to early for bad sectors. 

Also if I was to replace the drive how do I know what device is mapped to which sata port?  Is it as easy as sda = port 0, sdb = port 2?

---

### Post by ian dobson on 2010-01-18
Hi,

Shutdown your array then run a smart test for the dodgy drive. If the smart test shows anything then print the report out and return the drive with the report.

Bing new it could well be that the errors are OK as no drive is 100% OK and it could be that it's the first time the drive has tried to write to the bad sectors.

When I get a new drive I test it by filling it with "data" then run a smart test to see what state it's in.

The device number is sd (for SATA), a,b,c,d (for port number on the controller) 1,2,3 (for partition)

for example sdb1 (second harddisk, first partition).

Regards
Ian Dobson

---

