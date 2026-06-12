---
title: "crashed server. hard resets at detecting drives: scsi host0: ahci"
date: 2020-06-18
forum: Server Platforms
---

### Post by mathias-x on 2020-06-18
My  old ubuntu server crashed today, and now does not reboot.
It automatically resets with the last line shown being
  scsi host0: ahci

(I had to film the monitor with my phone to even see that)

When I tried an Ubuntu rescue CD it also crashes before it
gets into any useful mode

In expert mode ; cn select 'detect drives' from the menu to have it immediately
crash

Is there anything else I can test?

The server's IPMI has no information on drives, error logs etc that look useful
(this is a supermicro)

Drives are SATA SSD Samsung 850 which are on slot 0 1 and 4

---

### Post by guiverc on 2020-06-18
FYI: Looks like [https://askubuntu.com/questions/1251426/rescue-boot-crashes-exits-after-loading](https://askubuntu.com/questions/1251426/rescue-boot-crashes-exits-after-loading)

---

### Post by slickymaster on 2020-06-18
*Thread moved to **Server Platforms**.*

---

### Post by mathias-x on 2020-06-18
I got a bit further. I am able to boot the 16.04 CD (USB stick) and go into expert rescue mode (where i don't continue with the install but go to a shell after loading the addition installer modules

IN that I can see the first SDD (I disconnected the other two for now) just fine (at least list-devices disk  and 'list-devices partition' show the disk and its partitions. lvm also shows the root and swap partitions.  But as soon as I execute 'disk-detect' the server crashed hard, no output.

I was however able to go into 'rescue mode', skip disk-detect (just continue) and then run a shell off the first SSD (and then ecryptfs-recover-private my $HOME) and the other SSDs are also accessible this way. 

So I wonder what causes disk-detect to crash and more importantly, how to detect what it is in fact trying at that point (it does not seem to have a single-step mode or such)

---

### Post by LHammonds on 2020-06-18
Disconnect the disks and attach a new disk with a different cable and see if it crashes doing the same test.  If so, its the controller.  If not, put the original cable on and see if it crashes.  If so, its the cable...if not, its a disk.

Keep doing this isolate/test procedure until you identify the exact cause.

Wouldn't be a bad idea to do the memtest function as well.

I hope you have been making data backups to different media.

LHammonds

---

