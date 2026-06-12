---
title: "10mins to boot after rebuilding a r5 partition."
date: 2010-01-19
forum: Server Platforms
---

### Post by steven.jones on 2010-01-19
I have/had a working system that took maybe 20seconds to boot. However due to an oops with hardware (power cable fell out) I lost 2 disks in a raid5...so I had to rebuild it, now the new partition wont mount on boot and it takes 180seconds Plus to get a control-d prompt. If I remove the mount from fstab and reboot and then mount manually after a normal boot its perfect and works....so it appears something in the boot/mount process is confused....

The q is where do I start looking to fix this?

I suspect its the LVM looking at the ext4 system and getting upset that its isnt LVM'd? Is that possible? The original partiton was /dev/i2o/hda1 and was not lvm'd and neither is the new....so i dont see why....but the boot time is now silly...multiple 180 second timeouts!

regards

---

### Post by a9k3d on 2010-01-21
Check the logs, especially dmesg. I had a problem like this and it was a bad sector on one of the drive. It would take ten minutes of retries before the driver would give up on that sector and then disk was fine.

---

### Post by bolucpap on 2010-01-21
My guess is when you recovered from the error the UUID of one of your partitions changed. However the entry in the /etc/fstab file is still mentioning the old UUID, which makes the system look for a partition with that UUID until it times out. You can edit the fstab file and update the UUID's to reflect the current setup of your system, that should solve it. You can type ```
sudo ls -l /dev/disk/by-uuid/
``` in a terminal to find out which UUID's are currently in use in your system.

---

