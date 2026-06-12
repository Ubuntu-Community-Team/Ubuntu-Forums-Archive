---
title: "hotplug SATA not detected - 12.04 server"
date: 2012-06-06
forum: Server Platforms
---

### Post by Benaiah on 2012-06-06
Hi

I have a 12.04 server install with 3 hard drives, all SATA.

I have checked the MB and AHCI is enabled. I installed the server with AHCI enabled on the MB. 

When I remove a drive, it disappears from the system, when I plug it back in it does not appear in /proc/partitions even after a partprobe. I have looked around on the internet for a few hours and from what I can tell it should be detecting the drive automatically.


```
~# modprobe --list | grep ahci
kernel/drivers/ata/acard-ahci.ko
kernel/drivers/ata/ahci_platform.ko
```

```
~# lsmod | grep ahci
~#
```

What else should I provide and what suggestions do you have?

---

### Post by dcstar on 2012-09-08
> **Benaiah said:**
> Hi

I have a 12.04 server install with 3 hard drives, all SATA.

I have checked the MB and AHCI is enabled. I installed the server with AHCI enabled on the MB. 

When I remove a drive, it disappears from the system, when I plug it back in it does not appear in /proc/partitions even after a partprobe. I have looked around on the internet for a few hours and from what I can tell it should be detecting the drive automatically.
..........
What else should I provide and what suggestions do you have?

Add yourself to this bug:

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/153768](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/153768)

I just upgraded from 10.04 to 12.04 and what used to work now does not.

---

### Post by thinsoft on 2012-09-11
In case you are still having problems, and need a workaround, I had the same problem.  Drives were discovered as soon as plugged in in 11.04, but were only detected on the first hot-plug in 12.04.  This worked for me:

     # apt-get install scsitools
     # rescan-scsi-bus

The rescan-scsi-bus command found all my drives, (those already known and two previously undetected eSata drives) and dropped them into /proc/partitions.

rescan-scsi-bus is a shell file, so presumably you could cherry-pick the contents and grab just the commands needed for your eSata drives.  I didn't bother, since the command runs in about 10 seconds, and that is good enough for me.

The manual page for rescan-scsi-bus is [here]("http://manpages.ubuntu.com/manpages/precise/man8/rescan-scsi-bus.8.html").

Good Luck!

---

