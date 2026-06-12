---
title: "RAID0 Recovery"
date: 2007-12-06
forum: Server Platforms
---

### Post by lee_connell on 2007-12-06
my raid has 2 disks and one had been kicked out.  the system had been restarted and the 2nd disk was also kicked out saying it was "non-fresh" upon reboot.  I know the data is still on these drives.

mdadm just wont start the raid as it's "non-fresh" I know you can --force the raid to start but how do I do this when the raid /dev/md0 is my root and boot partition?

Do I start a livecd and do it from there?  How does this work so I can tell it to --force the startup so i can then resync and fsck the device.

thanks!

---

### Post by kidders on 2007-12-07
Hi there,

RAID 0 shouldn't really be called "RAID" at all ... all using it does is double (or more) the chances of a major failure, I'm afraid.

> How does this work so I can tell it to --force the startup so i can then resync and fsck the device.Because both your disks contain different data (ie there is no redundancy), there's nothing to sync. Most people would consider their data lost at this point ... especially since we're only talking about root & boot partitions ... but you may have some luck with forensic data recovery utilities or filesystem rescuers, depending on the filesystem type you're using. Thankfully, there are plenty of threads here on that topic. As you mentioned, booting from a CD is essential ... you can't perform repair/recovery operations on filesystems while they're in use.

If your personal files are okay though, I would recommend reinstalling from scratch (perhaps without RAID 0) ... it's likely to be faster and more reliable than a recovery.

---

### Post by umattu on 2007-12-07
IME do NOT use RAID 0, unless it is for a machine where performance matters, and you could careless about losing the data on the drives.

Just like Kidders said: RAID 0 doubles your chance for data loss!

---

### Post by lee_connell on 2007-12-07
I renamed my thread to raid1, i made a mistake there, it is a mirror not a stripe.  I ended up booting from a debian live cd and had to issue the command:  mdadm --create --force /dev/md0  --level=1 raid-devices=/dev/sda1 missing

something to that affect and it rebuilt the raid and i was able to reboot the machine and everything was fine.

---

