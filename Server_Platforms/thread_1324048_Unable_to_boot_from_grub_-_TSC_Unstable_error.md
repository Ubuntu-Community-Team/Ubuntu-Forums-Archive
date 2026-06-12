---
title: "Unable to boot from grub - TSC Unstable error"
date: 2009-11-12
forum: Server Platforms
---

### Post by steverowe on 2009-11-12
Hi, I need some help here peeps.

I run and install a live cd with no problems.

When my system reboots i get the following error when pringing up the CPU's

checking TSC syncronization [CPU#0 -> CPU#4]:
Measured 193009318208 cycles TSC warp between CPU's, turning off tsc clock.
Marking TSC unstable due to check_tsc_sync_source failed

at this point the system locks and needs to be reset ???
The system does not even get to the second bank of CPU's 5-8 before the error shows and the system locks up.

Any help appreciated. Is there a grub option i can use to help fix this boot problem?

SYSTEM info--

8x Hyper-threading Xeon 2.7ghz (total of 16 CPU's) 8GB DDR Ram registered EEC, 2x72gb SCSI 15000rpm non raid setup although on a raid controller as separate containers.

---

