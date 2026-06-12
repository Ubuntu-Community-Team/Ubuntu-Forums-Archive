---
title: "Software RAID w/ 1TB backup not on RAID"
date: 2011-04-09
forum: Server Platforms
---

### Post by electricbrewer on 2011-04-09
Hi,

I've come across a situation that I could use some guidance on solving.

I'm trying to set up a RAID 5 server configuration with 1 hot spare using 4 250GB hard drives.  In addition I want to use a 1TB drive as a backup that is not in the RAID configuration.  All drives are SATA drives.

I completed the installation using the 10.04 alternative CD.  I partitioned the 4 250GB drives the same and was able to create the software raid devices successfully.  For the 1TB drive, I just formated as ext3.

Now, here's my problem.  I can only boot into Ubuntu when the 1TB drive isn't connected!  Once the drive is connected, the computer cannot get to the Ubuntu splash screen.  I'm thinking that the separate 1TB drive confuses the RAID causing it not to boot. 

Any help would be greatly appreciated!

Thanks!

---

### Post by elico on 2011-04-10
it's related to you bios\setup settings of which sata HD your computer will boot the computer from.
these settings are depend on your Motherboard.
you can lookup in the bios "boot sequence" or "boot priority".

---

### Post by electricbrewer on 2011-04-11
Thanks for the response.  I did set up the boot order correctly in the bios.

In addition, I installed ubuntu on the 1TB with the root and /boot partitions and made the RAID 5 /home.  I still cannot boot into ubuntu.  This has me thinking that their is something up with the 1TB drive.  I should be able to boot from that one drive...

Thanks!

---

