---
title: "Random device-mapper / raid issues on boot"
date: 2007-08-18
forum: Server Platforms
---

### Post by deviantintegral on 2007-08-18
Hi,

I have a fileserver running with Ubuntu 7.04 with the following setup:

[LIST]
[*]4 SATA drives using the onboard ports
[*]4 SATA drives connected to a SiI 3114 PCI card
[*]md0 is RAID1 with a partition on each of the drives mounted on /boot
[*]md1 and md2 are RAID5, part of a LVM set for everything else
[/LIST]

Randomly (or so it seems) on boot up, I get one of the following errors:

md: array md0 already has disks! (spammed repeatedly until the initramfs drops to a shell)

or:

device-mapper: table: 254:0 linear: dm-linear: Device lookup failed
device-mapper: ioctl: error adding target to table

Which pauses until the timout is hit.

I would say about 1/3 of boots work fine, and 2/3 I get one of the above errors. Once the system is booted, everything works fine without any hints of a hardware or software issue.

Anyone else seen this? It feels like a bug with something, but I have no idea where to start troubleshooting.

Thanks,
--Andrew

---

### Post by mpadams on 2007-08-19
[https://bugs.launchpad.net/ubuntu/+source/evms/+bug/116820](https://bugs.launchpad.net/ubuntu/+source/evms/+bug/116820)

Check out this Ubuntu bug and try commenting out the given line of evms script.

---

### Post by deviantintegral on 2007-08-21
Yeah, I'm not using EVMS, just straight LVM, so that script doesn't exist on my system.

---

