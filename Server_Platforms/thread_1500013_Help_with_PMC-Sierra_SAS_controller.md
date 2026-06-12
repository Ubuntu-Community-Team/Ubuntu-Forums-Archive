---
title: "Help with PMC-Sierra SAS controller"
date: 2010-06-02
forum: Server Platforms
---

### Post by ARhere on 2010-06-02
WARNING:  I have been using Linux for over 5 years, but still consider myself a Linux-noob as I am a hardware design engineer, not a software engineer, so speak slowly! ;-)

I am attempting to get Ubuntu Server 10.04 working with a custom built NAS that my company designed using the PMC-Sierra SAS controller that is supported with the new kernel.  Below is the Kernel I am using and the SAS chip listed under lspci.
```
jabil@jabilU1:~$ lspci
...
06:00.0 Serial Attached SCSI controller: PMC-Sierra Inc. Device 8001 (rev 05)
jabil@jabilU1:~$ uname -an
Linux jabilU1 2.6.32-21-server #32-Ubuntu SMP Fri Apr 16 09:17:34 UTC 2010 x86_64 GNU/Linux

```
According to the kernel notes, the SAS chip drivers I am using are built into the kernel.  I am trying to get the SAS drives seen as JBOD (or ANY flavor of RAID is fine too) to demo this system to a customer.  I am missing an important step in between getting the chipset seen in lspci and something in /dev/ that I can mount.  What step is this?

-AR

---

### Post by ARhere on 2010-06-02
UPDATE:  Ok, I have read in the kernel release notes that the driver is actually implemented in the new 2.6.34 driver for the PMC SAS chipset.  Also I found an old Red Hat installation where a development driver was installed and all 12 SAS drives are presented in the /dev/ folder as /dev/sdb, /dev/sdc, etc...

SO... I am changing my question.  Assuming this works and I am presented with a bunch of 1TB disks in the /dev/ folder, how do I combine them all as one big RAID5 drive I can mount?

I am hoping this is an easier question.  :-)

-AR

---

