---
title: "Missing disk in md0 preventing kernel upgrade"
date: 2008-07-04
forum: Server Platforms
---

### Post by sjwk on 2008-07-04
Evening all,
I've borrowed one of the RAID1 mirrored disks out of my sacrificial hardy test box to replace a failed one in a more critical almost-end-of-life machine.

Initially the hardy box failed to boot, but searching on here found that 'mdadm -R /dev/md0' at the busybox shell solved that.

Since the machine had been off for a week or two, I did a package upgrade, but the kernel images failed due to lilo stamping its little feet about not being able to write to the MBR of the second disk.  As a result, no other packages will install now because apt-get wants to complete the stalled packages...

There seem to be several options but I can't figure out the best approach:

Lilo wants -H passing to it to tell it to stop having a hissy-fit and just install to the MBR of the one disk that is connected.  All well and good, but it's no good me doing that manually since that won't get the package installed, and I can't find any way of giving the kernel package postinstall script any arguments to pass to lilo.  As far as I can see, there isn't a lilo.conf equivalent to -H?

Having looked at mdadm, I should be able to tell it to remove the missing device.  In fact, 'mdadm /dev/md0 -r detached' should, according to mdadm(8), 'cause any device which is no longer connected to the system to be removed'.  That doesn't help either - the array still thinks it has two devices, even if it only knows what one of them is, and lilo is still sulking in the corner.

I don't really want to mess about turning it back into a standard  non-RAID disk since ultimately I'll want it back in RAID1 configuration as soon as I decommission another machine with the same size disk.

So, does anyone have any suggestions on how to either make the machine temporarily think there's really only one disk in the mirror, or how to get the postinstall script to pass an argument to lilo, or any other suggestion?

Cheers,
Steve.

---

