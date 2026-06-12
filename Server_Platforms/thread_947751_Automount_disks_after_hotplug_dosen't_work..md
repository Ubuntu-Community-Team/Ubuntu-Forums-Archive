---
title: "Automount disks after hotplug dosen't work."
date: 2008-10-14
forum: Server Platforms
---

### Post by pelle2004 on 2008-10-14
Hi,

I'm using Server version 7.10.

I can't get a logical volume to automount.
At startup the volume is mounted according to fstab.
But when I try to do some hotplug it dosen't work.

1. Unplugging the disk works ok. 
First I unmount the disk and then tell kernel to delete the device before I physically remove the disk.

2. Plug in the disk.
Physically insert the disk.
Tell kernel to rescan the scsi channel.
After that the logical volume appears at /dev/mapper/<volume>.
But it dosen't make the actual monting in the same way as at startup.

I guess it is in udev somewhere 

/Pelle

---

