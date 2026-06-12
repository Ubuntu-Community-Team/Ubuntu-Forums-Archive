---
title: "Make nautilus define unique mount points for unique storage devices"
date: 2008-06-20
forum: Ubuntu Brainstorm
---

### Post by rockin_goliath on 2008-06-20
When one plugs in a thumb drive or an external hard drive, the mount point is always defined as /media/disk, /media/disk-1, or /media/disk-n. While it is great that the devices are auto mounted, it is not to great that the same device might have a different mount point depending on what else is plugged in. This is very confusing for new users when they configure applications to use the directories of external devices, and then have the mount points for those devices change on them.

I propose that when a new storage device is plugged in, a unique mount point is defined for that particular device, so that whenever you plug it in again it will always have the same mount point. The default mount should be able to be changed by right clicking on the volume and clicking "Properties." The user should not have to change the volume properties themselves first, it should be done for them.

Usage Case:
Bill has all his music on his external hard drive and is mounted as /media/WD-Passport and has Rhythmbox configured to look in this directory. Instead of Rhythmbox getting confused when the mount point changes from /media/disk to /media/disk-1, it always looks in the default mount point for this device.

---

### Post by smartboyathome on 2008-06-20
This can already be done (supposedly) with Nautilus by going to Computer and renaming the partition. I haven't had luck with this, but it might work for you.

Other than that, I don't think this would be a good idea, as the devices might have more than one partition, and while the device itself might have a disk label, but if there are multiple partitions, and that changes, it can cause everything to go haywire.

---

### Post by jpka on 2008-06-20
IMHO, 'disk', 'disk-1' etc. is confusing.
If I try to imagine an ideal (auto)mounting subsystem for Ubuntu, it will have tree like this:
/media/ST3320620AS-5QF3HZ00 (HDD; name and S/N seen in 'hdparm -i' and on top cover on drive)
/media/ST3320620AS-5QF3HZ00/1-8GB-fat32       (sda1)
/media/ST3320620AS-5QF3HZ00/2-8GB-reiserfs
/media/ST3320620AS-5QF3HZ00/5-267GB-reiserfs  (sda5)
/media/Drive_SK_USB20-356F38AC (Flash drive; params seen in 'lsusb -v')
/media/Drive_SK_USB20-356F38AC/1-2GB-vfat  ...or '2GB-vfat', if only one partition
/media/srv.local/nfs-films  (NFS)
/media/srv.local/ftp-games   (ftp)

This almost ensures uniqueness of names even if multiple drives of same size & type is present. Thus mounting can be fully automatic, not confusing, and not need to rename folders or make GUI for naming.

Also I don't like using volume labels for naming, because many filesystems don't have it (reiserfs, NFS...) and labels often may be same on different devices, due to auto-labeling, etc.

---

### Post by yochaigal on 2008-07-10
Yes, I've also been pushing for this for some time.  Please vote here!

[http://ubuntuforums.org/showthread.php?t=728241](http://ubuntuforums.org/showthread.php?t=728241)

[http://brainstorm.ubuntu.com/idea/7805/](http://brainstorm.ubuntu.com/idea/7805/)

---

