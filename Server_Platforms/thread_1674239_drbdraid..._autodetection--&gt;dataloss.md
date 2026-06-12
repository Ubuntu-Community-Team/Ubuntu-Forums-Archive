---
title: "drbd/raid... autodetection--&gt;dataloss"
date: 2011-01-23
forum: Server Platforms
---

### Post by Pfannkuchen on 2011-01-23
Hello,

I created 5 drbd-mirrored pairs and assembled them to a RAID0 using mdadm...
 
How can I prevent any autodetection, auto-mounting and device-mapping? This nasty autodetection-functions may cause data-loss (for example if mdraid wraps up the source-devices before drbd is able to wrap them). 

The concerned Harddisks are plugable and I will eventually use them in other servers (in emergency cases). So, I want to assert that there exists no server, which destroys my data just because of this nasty autodetection-functions. 

My Questions:

1. How can I build an array, which will never be detected and assembled automatically? (certainly independent of the servers configuration!)

2. How can I build drbd-pairs, which will never be detected and mapped automatically? (certainly independent of the servers configuration!)

Edit: I built the RAID using raw disks instead of "fd" marked partitions (fd stands for RAID AUTOMATIC DETECTABLE). And I also built the array using the Option "--auto=no". But all this didnt purge the autodetection. And there is also the LVM-Engine which automatically grabs up VolumeGroups out of the wrong devices. 

Regards,
Sascha

---

