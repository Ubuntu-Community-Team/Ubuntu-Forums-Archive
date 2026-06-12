---
title: "Understanding fstab"
date: 2015-10-27
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2015-10-27
Running 14.04.  Computer works fine - but I'm trying to understand fstab.  This is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sdb5 14.04:
UUID=c0418788-5400-43d7-8d09-f10c5c411f6d	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb6 /home:
UUID=1c875897-0e34-42f0-8535-5cd7f5b39aff	/home	ext4	defaults	0	2
#Entry for /dev/sda1 BACKUP:
UUID=09DCC8751612A787	/media/backup	ntfs-3g defaults,uid=liz,gid=liz,dmask=002,fmask=113 0 0
#Entry for /dev/sdb8 HOMEFILES:
UUID=5C804D56804D3832	/media/homefiles ntfs-3g defaults,uid=liz,gid=liz,dmask=002,fmask=113 0 0
#Entry for /dev/sdb1 WINDOWS 7:
UUID=5045BA844151BA7D	/media/win7	ntfs-3g defaults,uid=liz,gid=liz,dmask=002,fmask=113 0 0
#Entry for /dev/sdb7 SWAP:
UUID=d6760f3a-087e-4068-a8c2-8cf5cdd49e6c	none	swap	sw	0	0
```


Why is it that when I look in media via nautilus (see attached) I get folders for **liz** and **sdb1**?    liz is the user name of this pc and sdb1 is the partition that win7 is installed in.   I can understand (I think) why the backup, homefiles and win7 folders are in the attached - because they are defined in fstab - but where have the other two folders come from, what defines them?  Note:  The two folders in media liz and sdb1 are empty.   Can I just delete them(?) - just trying to understand 'what' puts them there.

---

### Post by Morbius1 on 2015-10-27
I can explain half of the question.

If the system detects a partition that is not defined in fstab like when you insert a USB device for example it will automatically create a temporary mount point at /media/$USER/LABEL if there is a LABEL on that partition or /media/$USER/UUID if there is no label. When the partition is unmounted the /media/$USER folder remains.

$USER in this case is liz.

Why you have a /media/sdb1 folder I do not know.

---

### Post by coffeecat on 2015-10-27
I think I can explain the other half. Have a look at this thread of yours from over a year ago.

[http://ubuntuforums.org/showthread.php?t=2221622](http://ubuntuforums.org/showthread.php?t=2221622)

You were then mounting Windows on sdb1 onto /media/sdb1 until you changed your fstab. You probably created the /media/sdb1 folder yourself and then forgot about it when you abandoned using it as a mountpoint.

---

### Post by Quarkrad on 2015-10-27
Thank you - I think that original thread was a 'number of machine builds ago'.  I am gradually getting my head around some of this!

---

