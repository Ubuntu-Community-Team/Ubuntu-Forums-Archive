---
title: "Munged Raid1 drives"
date: 2010-12-03
forum: Server Platforms
---

### Post by JZMatrix on 2010-12-03
I had a system with 4 drives.  2 were 'stand alone' drives with a nightly DD clone between them (the root/boot drive and it's clone).  The second 2 were terabyte drives in a RAID1 configuration.

Long story short, the secondary clone drive was removed from the box though the nightly DD process was not, so the first terabyte drive ended up having the boot drive cloned over it breaking the raid (obviously).

From what I can tell, the raid on the second drive is still (mostly) intact, though (thus far) I have been unsuccessful with mounting the raid partition to get at any of the data.

I've gone through verifying that mdadm sees the partition on the second raid drive (the first drive is pretty much toast since 40G of it are known to be overwritten due to the dd).  fdisk shows that /dev/md0p1 exists, but is labelled as an autoraid partition and not listed as ext4.  And any attempts to mount either /dev/md0 or /dev/md0p1 fail (even when specifying the filesystem type).

My next steps were to attempt to attempt using the various disk scanning tools (testdisk, etc) to see if anything recognizes the drive.

Does anybody have any other, hopefully more direct means, of isolating the raid partition and hopefully being able to mount it to recover the data?

---

