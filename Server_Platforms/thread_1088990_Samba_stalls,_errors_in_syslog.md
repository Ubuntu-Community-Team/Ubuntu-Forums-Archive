---
title: "Samba stalls, errors in syslog"
date: 2009-03-06
forum: Server Platforms
---

### Post by kextyn on 2009-03-06
I really have no clue what's going on here.  This has been going on for a while but I finally decided to check the logs to see what was happening.  I have a 7 drive RAID5 array (Linux software RAID) which is shared out with Samba.  When I'm doing a lot of transferring to/from the array it tends to stall for 5-20 seconds before continuing like nothing happened.

Here's an example of what I've been getting in the syslog when this happens:
```
Mar  6 15:58:56 SERVERNAME kernel: [2825517.547053] ata8.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Mar  6 15:58:56 SERVERNAME kernel: [2825517.547104] ata8.00: cmd 35/00:08:bf:4b:38/00:00:3a:00:00/e0 tag 0 dma 4096 out
Mar  6 15:58:56 SERVERNAME kernel: [2825517.547105]          res 40/00:00:01:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Mar  6 15:58:56 SERVERNAME kernel: [2825517.547190] ata8.00: status: { DRDY }
Mar  6 15:58:56 SERVERNAME kernel: [2825517.547215] ata8: hard resetting link
Mar  6 15:58:56 SERVERNAME kernel: [2825518.050041] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Mar  6 15:58:56 SERVERNAME kernel: [2825518.110051] ata8.00: max_sectors limited to 256 for NCQ
Mar  6 15:58:56 SERVERNAME kernel: [2825518.170064] ata8.00: max_sectors limited to 256 for NCQ
Mar  6 15:58:56 SERVERNAME kernel: [2825518.170068] ata8.00: configured for UDMA/33
Mar  6 15:58:56 SERVERNAME kernel: [2825518.170079] ata8: EH complete
Mar  6 15:58:56 SERVERNAME kernel: [2825518.172063] sd 7:0:0:0: [sde] 976773168 512-byte hardware sectors (500108 MB)
Mar  6 15:58:56 SERVERNAME kernel: [2825518.187369] sd 7:0:0:0: [sde] Write Protect is off
Mar  6 15:58:56 SERVERNAME kernel: [2825518.187371] sd 7:0:0:0: [sde] Mode Sense: 00 3a 00 00
Mar  6 15:58:56 SERVERNAME kernel: [2825518.187420] sd 7:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  6 16:00:01 SERVERNAME /USR/SBIN/CRON[31599]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Mar  6 16:00:01 SERVERNAME console-kit-daemon[31598]: CRITICAL: cannot initialize libpolkit

```

And here's some more:
[http://stuff.kextyn.com/errorlog.txt](http://stuff.kextyn.com/errorlog.txt)

---

### Post by Vegan on 2009-03-06
Could be a RAID issue, are the disks healthy?

:guitar:

---

### Post by kextyn on 2009-03-07
As far as I can tell the drives are healthy.  I have used smartctl to check and they're all healthy.  I have 5 of these drives and they're all connected to the same PCI-X controller but only 3 are showing up in syslog.  Mdadm is also showing everything to be fine.  Can you recommend any other tests I can perform within Ubuntu?

---

### Post by kextyn on 2009-03-07
I just found this with Google... (maybe I used the wrong search terms before)

[https://bugs.launchpad.net/ubuntu/+bug/219786](https://bugs.launchpad.net/ubuntu/+bug/219786)

But I still don't see a solution.

It may also help to mention that I'm running Ubuntu 8.10 Server x64.

---

### Post by kextyn on 2009-03-07
Ok, after a little more searching it appears it could be the sata_mv driver.  From what I have read it's a problem in 2.6.27/28 kernels.  Here is a thread which may help me...if I knew how to install the patch:

[http://blogaristoo.lqx.net/index.php/2009/02/25/marvell-mv88sx6081-troubles-under-newer](http://blogaristoo.lqx.net/index.php/2009/02/25/marvell-mv88sx6081-troubles-under-newer)

The card I'm using is a Supermicro AOC-SAT2-MV8 which uses the MV88SX6081 chipset.  On the page that this guy links to ([https://bugzilla.redhat.com/show_bug.cgi?id=462425](https://bugzilla.redhat.com/show_bug.cgi?id=462425)) the guy who fixed it said it's already in the latest 2.6.27 kernels.  How can I tell if it's already patched in my kernel?

---

### Post by kextyn on 2009-03-07
I talked to Matt from [www.lqx.net](www.lqx.net) and he provided me with a patched module for 2.6.28.  Of course if I wanted to run that I'd need to either upgrade to Jaunty alpha or figure out how to install 2.6.28 in 8.10.  I think the later 2.6.27 kernels have this patch already but they aren't in the repos and I have no idea how to go about getting a newer kernel.  What would be the best way (and easiest) to go about patching the sata_mv module?  I've never compiled my own kernel so I'd be completely lost with that.

---

### Post by kextyn on 2009-03-13
I ended up compiling a kernel for the first time ever to fix this problem.  The changelogs at kernel.org show the bug being fixed in 2.6.27-15.  I went ahead and compiled the 2.6.27-19 kernel and all seems to be well.

---

