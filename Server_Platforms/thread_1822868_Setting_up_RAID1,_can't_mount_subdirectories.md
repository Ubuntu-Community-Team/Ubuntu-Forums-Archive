---
title: "Setting up RAID1, can't mount subdirectories"
date: 2011-08-11
forum: Server Platforms
---

### Post by i2dave on 2011-08-11
This is a very odd problem, which I've not experienced before!....

I've set up 10.04 LTS Server, on a system with the following config:

Disk 1 (/dev/sda) - primary boot & swap

Disk 2 (/dev/sdb) - Data disk - 3 partitions, each raid1
Disk 3 (/dev/sdc) - 2nd disk in raid1 setup

The system boots up fine using disk 1, which is as expected.

The problem appears with the raid1 mirrors - I've manually added them after installation using mdadm, and they're all setup properly and can be seen using mdadm --details --scan

Each mirror disk has 3 partitions, and I want to mount them thus:

partition 1 - /web
partition 2 - /web/a
partition 3 - /web/b

If I mount /web, then the other 2 partitions are invisible.  You'd think this was logical, but I've always been able to set servers up this way from initial install, with 2nd mounts on subdirectories!  For example, I have another webserver which was interactively installed from CD, and has mounts of /web, /web/a, /web/b that all work fine from fstab.....

Is it the manual setup that's stopped it?  

Any thoughts appreciated....

---

### Post by YesWeCan on 2011-08-13
I don't know. But you have waited for an answer for 2 days so I thought I'd have a go. :)

I gather what you are relying on is the kernel to bring up md0 (or whatever) first and mount it, then bring up md1 & md2 and mount them to subdirectories of md0. Is that right?

So I'd want to see fstab and mdadm.conf and sudo blkid. Did you update initramfs? And obviously - do the mount points a & b exist in md0?

---

