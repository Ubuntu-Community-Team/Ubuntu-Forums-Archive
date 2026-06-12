---
title: "Trouble setting up RAID mirror"
date: 2005-12-17
forum: Server Platforms
---

### Post by spectre_25gt on 2005-12-17
I've got a Promise Fasttrack 376 in my box which I've been using with windows to keep my data in a bit more secure space. Now that I'm finally moving to linux, though, I'm running into some issues. It doesn't look like that "RAID" controller is actually supported at all... 

Anyway, I've pretty much given up on that. So, I backed up my data, split the mirror into two singe stripes (only way to get the drives to read correctly. I really hate Promise at this point) and I'm trying to get software raid running. I created Linux RAID Auto partitions on both drives and used mdadm to create the array. The trouble is, when I go to create the LVM partition on the drive I end up with fdisk saying that it couldn't reread the partition. It fails with an error of 22.

After a reboot, everything actually seems to look ok. If I go back into fdisk, it shows the correct partition there and everything (/dev/md0p1 Linux LVM). So, I tried formatting the drive with "mkreiserfs." Unfortunately, that fails on me with an error of "Stat of the device '/dev/md0p1' failed."

I'm pretty much lost on what to do here. This is my first time working with software RAID on linux. I'd love to just purchase an internal raid subsystem, but I just don't have the funds right now.

---

### Post by spectre_25gt on 2005-12-17
Well, I figured out my mistake. Turns out /dev/md0 doesn't need to be partitioned. I guess I should have tried that before posting, but I just didn't think about it then.

I did get an error saying "raid array is not clean -- starting background reconstruction," though. Is that anything to be worried about?

---

### Post by Glut on 2005-12-19
That's to be expected.

---

