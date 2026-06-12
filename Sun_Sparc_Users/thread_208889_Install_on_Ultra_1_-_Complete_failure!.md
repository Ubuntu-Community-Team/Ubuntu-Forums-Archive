---
title: "Install on Ultra 1 - Complete failure!"
date: 2006-07-04
forum: Sun Sparc Users
---

### Post by exobuzz on 2006-07-04
So, I ran into the esp problems. I managed to get it installed though by manually loading the esp module. ok.

But I am unable to continue the process to create a fixed initfs.

I booted from the install cd in rescue mode. I modprobed the esp module. Driver reports my partitions. Only need to mount them. But i cant?!

mount /dev/sda1 /boot/ complains about the syntax and in the logs you see its trying to use cramfs. ok.. so

mount -t ext3 /dev/sda1 /boot
causes a no such device! nothing in the logs. the device is there. i can dd data from the scsi partition. the ext3 fs is included in the resuce cd right ?

Anyway. Enough of this. reinstalling debian.

---

