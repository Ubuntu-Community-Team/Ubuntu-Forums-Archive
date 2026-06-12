---
title: "How do I mount external media with &quot;fake permissions&quot;?"
date: 2009-11-07
forum: Security
---

### Post by entropy1 on 2009-11-07
I have a dual-boot Vista/Ubuntu system.  In my fstab file, I have the line

/dev/sda3 /media/C ntfs-3g quiet,defaults,rw,uid=myname,gid=myname,fmask=177, dmask=077 0 0

to automatically mount my Vista NTFS partition so that files appear to have the indicated permissions.  This is useful because when I copy a file from the NTFS partition to my Ext3 home directory, the file will come with the permissions I want.

My question is: How can I accomplish the same permission trick with my external USB-connected hard drive (NTFS) or my USB flash drive (FAT32)?

---

### Post by bodhi.zazen on 2009-11-07
You can do the same thing, add an entry in fstab, with the same options, for your removable drives.

since the location (dev/sdxy) can change, mount by label or uuid

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by entropy1 on 2009-11-07
Thank you bodhi.zazen.

Unfortunately, after I changed fstab as you suggested, when I remove and reinsert the flash drive, I get the error that I don't have the privilege to mount.

Then I removed the line from fstab so that I could click on the drive in places in nautilus.  When icon appeared on my desktop I right clicked and selected the volume tab and clicked on settings and tried to change the mount options.  I unmounted and removed the drive.  But now when I insert the drive it doesn't mount because the option uid is malformed.  How can I fix this?  Where is the setting information stored - so I can remove it?

Answer: The setting information is in /home/<username>/.gconf/system/storage/
Remove the storage directory; logout; login again to solve problem.

---

### Post by entropy1 on 2009-11-07
After experimenting with pysdm, I found that

UUID=1516-011E  /media/PRSNL  vfat  uid=myname,gid=myname,noauto,dmask=077,user,fmask=177  0  0

works for my flash drive.  The change is adding the options "user" and "noauto".

However,

UUID=F6C0C363C0C328A7  /media/Iomega_HDD  ntfs-3g  uid=myname,gid=myname,noauto,dmask=077,user,fmask=177 0  0

does NOT work for my external USB-connected hard drive; I get the error

Cannot mount volume.

Unprivileged user can not mount NTFS block devices using the external FUSE library.  Either mount the volume as root, or rebuild NTFS-3G with integrated FUSE support and make it setuid root.  Please see more information at [http://ntfs-3g.org/support.html#unpriviliged](http://ntfs-3g.org/support.html#unpriviliged)

---

