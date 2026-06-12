---
title: "restoring windows from a disk image"
date: 2007-04-07
forum: Windows
---

### Post by insane_alien on 2007-04-07
Hey, i made an image of a harddrive as a backup in case i borked something while installing gentoo on it for a friend. and well, it got borked. i tried using dd to copy it back onto the drive but when i try to boot it gives an 'invalid partition table' error. i tried to fix it with gparted and when i chose to format the whole disk as NTFS it gave a bunch of errors about how you can't have a partition table outside the disk.

does anyone know how to fix this?

i'm not gonna be popular if this doesn't work.

another thing, would it be possible to just format the drive as NTFS mount the partition from a live CD and copy and paste the files over? obviously i would have to get my XP CD out and do a fixmbr . but woul it work?

---

### Post by motin on 2007-04-15
> **insane_alien said:**
> Hey, i made an image of a harddrive as a backup in case i borked something while installing gentoo on it for a friend. and well, it got borked. i tried using dd to copy it back onto the drive but when i try to boot it gives an 'invalid partition table' error. i tried to fix it with gparted and when i chose to format the whole disk as NTFS it gave a bunch of errors about how you can't have a partition table outside the disk.

does anyone know how to fix this?

i'm not gonna be popular if this doesn't work.

another thing, would it be possible to just format the drive as NTFS mount the partition from a live CD and copy and paste the files over? obviously i would have to get my XP CD out and do a fixmbr . but woul it work?

I don't know how you made the image in the first place. I use DriveSnapshot for Windows to make images of each partition and restore partitions one by one when needed, so I can't help you there. 

Refrain from copying all files - it is so easy to miss files when doing this - it will probably be more a waste of time. If you however get all files including hidden and system files in the right place as well as the windows kernel etc the system will probably boot as expected. In case you change your partition table however you might have to change hd-paths in boot.ini first. 

Check out the [UBCD for Windows]("http://www.ubcd4win.com/") - maybe that will help?

What happens if you use gparted to first delete all partitions, rebooting and then going for either image restore or ntfs-formatting?

---

