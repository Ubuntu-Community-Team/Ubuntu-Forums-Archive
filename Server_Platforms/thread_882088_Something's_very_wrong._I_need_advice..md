---
title: "Something's very wrong. I need advice."
date: 2008-08-06
forum: Server Platforms
---

### Post by MountainX on 2008-08-06
I just set up a new file server with Hardy 8.4.1. Performance is really bad. I am overwhelmed by the problem and I don't really know what to do next.

I'm seeing errors in dmesg, but I can't seem to narrow anything down. I'm attaching all the information I can think of and I would appreciate any suggestions on how to fix this server. It is meant to replace an older Windows server, but the Ubuntu server performance is worse by a factor of 10! It must be due to serious errors somewhere (or many places?).

The main symptom of the problem is slow disk performance. 
```

/dev/mapper/sdX_crypt:
 Timing cached reads:   1378 MB in  2.00 seconds = 688.89 MB/sec
 Timing buffered disk reads:  166 MB in  3.01 seconds =  55.12 MB/sec

/dev/mapper/sdX_crypt:
 Timing cached reads:   1368 MB in  2.00 seconds = 683.69 MB/sec
 Timing buffered disk reads:  170 MB in  3.02 seconds =  56.37 MB/sec

```

The GUI is also very slow (yes, I'm running Ubuntu desktop on this server).

The following info is included in the attachment

2008.08.06.df.txt     
2008.08.06.lspci.txt      
2008.08.06.dmesg.txt           
2008.08.06.lspci-vvn.txt 
2008.08.06.fstab.txt 
2008.08.06.lsmod.txt           
bonnie.output.txt
bonnie.output.html
HardwareSpecs.txt

---

### Post by moonpup on 2008-08-06
It looks from dev/mapper that you possibly encrypted some partitions? Is that a correct assumption?

---

### Post by MountainX on 2008-08-06
> **moonpup said:**
> It looks from dev/mapper that you possibly encrypted some partitions? Is that a correct assumption?

yes, 5 encrypted partitions

however, there is one drive that is not encrypted. It is a Samsung HD103UJ as a passthrough on the Areca controller. It does perform better, but cached reads still seem slow. Here's the typical hdparm output for the no-crypto drive:

/dev/sdX:
 Timing cached reads:   1460 MB in  2.00 seconds = 729.62 MB/sec
 Timing buffered disk reads:  290 MB in  3.02 seconds =  95.89 MB/sec

---

