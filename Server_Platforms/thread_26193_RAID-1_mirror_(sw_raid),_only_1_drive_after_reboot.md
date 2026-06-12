---
title: "RAID-1 mirror (sw raid), only 1 drive after reboot"
date: 2005-04-12
forum: Server Platforms
---

### Post by sreid on 2005-04-12
I have a RAID-1 software RAID setup with two disks. The problem is, it forgets the second disk after reboot, so I have to manually add it with "sudo mdadm --add /dev/md0 /dev/hdc1". That works but is less than ideal as it requires a resync.

Backstory: Coming from Debian, where this was set up fine. I repartitioned ONE of the two drives and installed Hoary on it. During the install I told it to create a RAID-1 array with 2 devices, but (violating the instructions on the screen) I intentionally only gave it a single device to use. I was impressed that that actually worked. The OS installed to that device fine, and /proc/mdstat showed a raid1 mirror with the [U_] thing showing that one device was up and one missing (as expected). I copied my old files over from the other drive, and once I was satisfied that I could ditch my old Debian install, I created a single software raid partition on that disk and added it to md0. All worked great until I rebooted, when it came up with only the first drive. 

Here is my /etc/mdadm/mdadm.conf. I added the ,/dev/hdc1 by hand, but that doesn't seem to have had any effect.

```
DEVICE partitions
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=6847c607:6f153c99:342b19c5:d759eb58
   devices=/dev/hda1,/dev/hdc1

```

The drives are two 200GB, each with a single partition spanning the whole drive. The resulting md0 device contains my root (and only) filesystem.

---

### Post by tonym on 2005-04-12
How did you create your initrd file?  When mkinitrd is run (either by you or automatically when a new kernel is installed ) it includes mdadm commands to start the RAID1 array at boot so it can access root.  It creates the array with the partitions that existed when mkinitrd was run.  Thus if only one mirror was in place it only starts the array with one mirror subsequently.

If this is the problem you need to run mdadm to add the second mirror and then run mkinitrd,  either by hand or possibly (I'm not sure) by dpkg-reconfigure on your kernel package.

Regards

Tony.

---

### Post by sreid on 2005-04-12
Thanks! "sudo dpkg-reconfigure linux-image-2.6.10-5-386" did the trick.

---

