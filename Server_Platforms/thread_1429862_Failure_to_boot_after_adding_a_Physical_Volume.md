---
title: "Failure to boot after adding a Physical Volume"
date: 2010-03-14
forum: Server Platforms
---

### Post by DuronForever on 2010-03-14
> Tl;dr version: Why oh why does the kernel only automount two out of the three necessary raid1 volumes before moving on to LVM startup, when I add a third necessary one to a previously working system with two?

My server is set up with the root volume on LVM-over-dmraid1, and I have found a rather serious issue with that.

The system disks are sda and sdb (currently a 500 and a 320), each containing, in order, some swap (simply mounted as 2 swap partitions), a small raid1 block (md0) used as-is as /boot, a large raid1 block (md1) used as the PV for VG labeled system, which contains LVs for / and /var, and more or less empty space. In addition, there are data disks running as md3, which is the PV for VG storage.

I wanted to expand the VG system, using it for a couple of extra partitions. I created, on the empty space of the system drives, a second raid1 set (/dev/md2), added it as PV, and went on my merry way. I also did a whole bunch of other things, which conspired to make the troubleshooting that followed somewhat tedious.

It turns out that this action caused my system to be unable to boot. In particular, the kernel (before mounting root) apparently starts up /dev/md0 and md1, but then it moves on to starting lvm without starting md2 (despite them being on the same drives, even). LVM, only finding one of the two PVs of the VG system, refuses to start the VG and promptly everything dies due to not having a root.

I fixed this (eventually, once I had almost accidentally figured out what had happened) by booting into a Live CD, adding the spare 180 gigs at the end of the larger disk to the VG without raid in between, and pvmove-ing the new volumes I'd already installed on it, and vgreduce-ing md2 out of it. This caused the whole thing to suddenly happily boot again.

Is there a config file somewhere that determines which raid volumes get assembled early? If so, which?

One theory I have is that it's one of the files in /boot, which would imply that if you add a PV to the VG which contains root, you need to essentially reinstall your kernel or do something non-obvious that regenerates the configs afterwards, before the next boot.

Anyone know?

{edit to add: Yup. Vgextend and then apt-get remove <latest kernel>, apt-get install linux-server works as a workaround. Presumably there is an easier way to regen all those accompanying config files in boot, but I don't know it.}

Background:

This system was installed originally as an 8.04.1 server install, then upgraded due to other problems using the alternate CDs to 8.10, 9.04, and 9.10, then dist-upgraded as network was available again.

md0 : active raid1 sda2[1] sdb2[0]
md1 : active raid1 sdb3[0] sda3[1]
md2 : active raid1 sdb4[1] sda5[0]
md3 : active raid5 sdf1[3] sdc1[0] sde1[2] sdd1[1]

/dev/mapper/system-root on / type ext3 (rw,relatime,errors=remount-ro)
/dev/mapper/storage-main on /storage/main type ext3 (rw,relatime)
/dev/mapper/system-mail on /var type ext3 (rw,relatime)
/dev/mapper/system-VMimages on /var/lib/libvirt/images type ext3 (rw,relatime)
/dev/md0 on /boot type ext3 (rw,relatime)

---

