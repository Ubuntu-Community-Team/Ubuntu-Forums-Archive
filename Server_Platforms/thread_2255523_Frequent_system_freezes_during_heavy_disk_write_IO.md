---
title: "Frequent system freezes during heavy disk write I/O"
date: 2014-12-05
forum: Server Platforms
---

### Post by Chris on 2014-12-05
This is a server that I recently upgraded with a new motherboard and processor. It's running Ubuntu 14.04 on a ASUS Q87M-E motherboard with Haswell i3-4130T (this has the AES-NI extensions). The RAID array is the same one that ran on the old machine. It's 5 2TB SATA drives of various makes (they're all 100+MB/sec drives), software RAID6, cryptsetup/luks on top of the array, then XFS. Most of the drives are low-end "green" types but with all power management features disabled (ie. they are not sleeping. there is no load_cycle_count increases).

As far as the disk array the old system ran great but the motherboard and processor was 10+ years old. On the new processor/motherboard it's experiencing massive system freezes while writing to the array (anything, untaring something, rsync, whatever). With "heavy"(*) write activity it will run for 30 seconds then the whole system will freeze for 30 seconds to 2 minutes, then run 30 seconds, then freeze, etc. Disk, network, video, everything, totally unresponsive... There are no messages in the kernel logs or anything. iotop reports low i/o activity (at least until it freezes).

Possibilities I'm thinking of: Something to do with the Intel disk controller (the old system was running 64-bit PCI Adaptec SATA controllers in JBOD mode). Something to do with cryptsetup AES-NI (the old system did not have this). Maybe a drive or two is going bad (but normally you could see this in the kernel log when it stalls). Or something else to do with the motherboard (BIOS, etc).

Anyone have any ideas? It could just be a BIOS or kernel setting that could improve things, I don't know. Reading from the array does not cause any issues. It is making this server unusable though because it's whole purpose is moving large chunks of data around (1TB databases and such).

(*) It actually only takes about 25-50MB/sec to freeze up the system. This a fraction of the array's throughput although the old system was much faster in raw array speed, about 400MB/sec max whereas this new one is only 200MB/sec or so. However, with the encryption the old system could only manage about 100MB/sec, the new one can run the array with encryption at nearly the same speed as the raw array (200MB/sec).

---

### Post by lukeiamyourfather on 2014-12-05
I would run a system memory check and I'd double and triple check logs and dmesg for errors. Chances are either there's a bad stick of memory or perhaps an issue with the storage (bad drive controller, bad cable, loose connection, etc.). Is the power supply appropriate for the machine?

---

### Post by Chris on 2014-12-05
It's using a PC Power and Cooling 610W power supply which has stably powered many systems over the years. The whole system pulls 70W under load so I don't think that's an issue. :) This is all low-power stuff picked specifically for it's low power consumption (look up this motherboard and CPU).

Memtest was run for 120 hours, and the system was run under load for 2 months before even assembling it in its final form, as this is a critical server. I don't think that is an issue. :) It's running G.SKILL Ripjaws RAM.

Bad drive controller would be the motherboard Intel chipset itself. Possible but I have never seen it. I have tried replacing all the SATA cables but no change (I tried various "SATA2" and "SATA3" cables just because I had them; Like I mentioned though, the old system ran great with this exact setup except for the motherboard and CPU).

---

### Post by tgalati4 on 2014-12-06
Any hints in the log files?  I would  run an *ssh* session from another machine and examine the processes.  If you are getting a lot of System% during heavy writes, then it could be simply a mismatch between the processing speed of a new CPU and the older hard disk buffers.  One would expect the hardware to be compatible, but mixing old and new can cause strange issues.

If the data is important, I would use brand-new, enterprise-class disk drives and simply migrate the data to a new RAID pool.  Keep the old pool as a backup for a while.  Repurpose the old drives for static storage.

---

### Post by Chris on 2014-12-07
The array actually was rebuilt on new drives with the latest mdadm/etc a short time before moving off the old server. So it's running the most current formats.

There is nothing unusual in the logs at all. That's the difficult thing about this. top, iotop, console, and other things I have tried show nothing. There is very little load according to those tools. I have even tried connecting via serial console (although I have not tried debugging the kernel via that method which may be my only choice at this point).

---

### Post by Chris on 2015-01-04
Seems to be a bit better with recent kernel releases but the issue is still present.

---

### Post by Chris on 2015-08-31
Going on 10 months, still seeing this issue. I tested with disabled AES-NI and no change so it's not that. I have switched to an Areca 1260 controller and same problem so it's probably not related to the controller either.

Seems like it might be XFS related. I'm not sure. It's weird though because I have another machine running a very similar setup except with much older hardware and it runs perfectly with no freezes. It also uses RAID6/dmcrypt/XFS same version of Ubuntu. It's an old IP35 mobo with Q9550.

---

### Post by tgalati4 on 2015-08-31
It's possible that the low-power i3 (and supporting chipset) is not a good match for a large RAID6 pool running XFS, where the Q9950 runs fine.  Could be similar to trying to crunch numbers with a Celeron processor versus a Xeon.  All it takes is one bottleneck.  You do mention that the new system runs faster than the old with encryption--that is interesting.

Reading this blog gave me some insight into the difficulties at achieving maximum, theoretical RAID speeds:  [https://calomel.org/zfs_raid_speed_capacity.html](https://calomel.org/zfs_raid_speed_capacity.html)

Perhaps your "Green" drives (even though spin-down is turned off) are interfering with maximum throughput.  There are other things going on with "Green" drives that would not show up in log files, but a timing struggle between the SATA controller and the drive's firmware.  A better comparison would be setting up the RAID6 with identical, enterprise-class, expensive, spinning hard disks.

---

