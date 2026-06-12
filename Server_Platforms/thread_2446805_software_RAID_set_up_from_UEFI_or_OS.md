---
title: "software RAID: set up from UEFI or OS?"
date: 2020-07-07
forum: Server Platforms
---

### Post by mustermark on 2020-07-07
Hi,
I'm tying to build a small server for personal backups, and being relatively new at this I have some doubts about the set up. The main one at the moment is about the disk configuration. My idea was to have one small ssd for the OS (ubuntu server, of course) and two large hdd in RAID 1 for the data. The server I've bought is the HPE microserver gen10 plus, without the optional RAID controller, so my options to configure the software RAID are either do it though the UEFI or do it during the OS installation. My questions are, first, does the configuration I had in mind make sense? And second, is there any difference, in performance, reliability or management simplicity, between setting up the RAID one way or the other?

Thanks!
Pablo

---

### Post by TheFu on 2020-07-07
RAID for a backup?  Really?  Spend the RAID effort on the primary storage, where you need it.
Some HP systems don't work well with Ubuntu.  I've seen formerly certified-for-ubuntu HP system fail to boot the next LTS release.

If the MB provides the RAID, that is called "FakeRAID" and should almost never be used. FakeRAID really should be avoided with only a very tiny sliver of reasons for it to be used. You haven't mention any of those reasons.

SW-RAID is very flexible, but I'd only bother with it for primary storage, not backup storage.  RAID solves 2 problems - performance and HA.  Backups don't need either.  Spend the effort on having well created, tested, validated, backups. That's hard enough.

---

### Post by darkod on 2020-07-07
I am not familiar with setting up "raid through uefi", didn't even know it exists.

But for SW raid I tend to recommend using mdadm in ubuntu. And to use partitions as array members, not the disks themselves (create one big partition on each disk, unformatted, and use that as raid member).

The main benefit I see from this is that you can connect those disks to any computer later, and read the data (assuming the data itself is not corrupted of course). The array made by mdadm will not be linked only to the computer where it was created, it is readable by any computer.

For other HW or semi-HW setups you might depend on the computer itself, and depending on the case the array will not always be readable if you simply move the disks to another computer.

Honestly I have never compared mdadm performance with other options, but for basic home setup I find it enough and enjoy the flexibility.

---

### Post by mustermark on 2020-07-07
Thanks TheFu and Darko!
First, I don't know why I said backup, it's not meant to be backup but main storage, sorry for the confusion! I guess I said backup because I'm trying to collect in one place stuff that is currently distributed over many different places (work computer, a bunch of old portable disks, the cloud, ...).
Regarding the machine, I've seen some reviews of it that say that ubuntu server worked on it "out of the box" so fingers crossed!
Finally, thanks for your help, I guess I'll then opt to configure the RAID directly on ubuntu.

---

### Post by TheFu on 2020-07-07
Be certain you don't forget the backups.  For some RAiD problems, the best answer is to wipe the array and restore from backups. You can search these forums for people having issues with RAiD because they go confused and didn't do backups too.

---

