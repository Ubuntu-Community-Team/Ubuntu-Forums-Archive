---
title: "raid1 with mdadm and dmcrypt."
date: 2008-05-09
forum: Server Platforms
---

### Post by finite9 on 2008-05-09
Ive just wiped a couple of new 500GB eSATA disks with "badblocks random" which took nearly 48 hours!  and now I want to setup RAID1 on them, but my intention is to have them RAIDed, with dmcrypt and LVM on top.  What is the best way to do this?

Should I mdadm them now then setup dmcrypt on top, then lvm or should I dmcrypt them first then setup raid1?

I am very familiar with dmcrypt and lvm and use this on a few other desktops/servers but im new to software raid

I partitioned them with gparted, without installing a filesystem.  Do I need to partition them in any special way for them to be used as a RAID array?

---

### Post by sudo_sk0 on 2008-05-10
kindly post your question here
http://ubuntuforums.org/showthread.php?t=788713

asking in 1 thread will get us more attention.

---

### Post by finite9 on 2008-05-13
not that easy to accomplish this :) I have got it working but reboot makes system non bootable, because the kernel autodetection of the array does not recognise the newer 1.0 metadata superblock format.  I am unbootable right now, because fsck will not start system even though the file system that fails the check has nothing to do with /, /boot or /usr or /home!!

Once I have managed to edit my fstab so that I can boot again, I will put up a guide explaining how to do this, with the old metadata format.  I am actually doing this on a CentOS 5.1 server, not Ubuntu, but the procedure is the same, but it may be possible for the newer 2.6.24 kernel on hardy heron to recognise the newer metadata format at kernel boot.  On CentOS I am running 2.6.18-53, but it's weird that I managed to create the array, dmcrypt mapper and lvm mapper and mount the file system without anything complaining!  Seems like it's just the autodetect boot sequence that fails.

---

