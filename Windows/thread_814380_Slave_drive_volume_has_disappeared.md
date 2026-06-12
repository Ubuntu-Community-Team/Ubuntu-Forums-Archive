---
title: "Slave drive volume has disappeared"
date: 2008-05-31
forum: Windows
---

### Post by mariann53 on 2008-05-31
My slave drive volume disappeared after installing a new Windows Xp  SP2. I looked at disk management but i can only delete it nothing else. I use it for all my Media files 500GB. Can anyone help PLEASE

---

### Post by Rocket2DMn on 2008-05-31
Are you currently in linux?  If so, post the output of
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```

---

### Post by mariann53 on 2008-05-31
No I'm using Windows Xp sp2

---

### Post by Rocket2DMn on 2008-05-31
Then you are asking in the wrong place.  You can try posting in the Windows Discussions subforum at [http://ubuntuforums.org/forumdisplay.php?f=170](http://ubuntuforums.org/forumdisplay.php?f=170)
It is possible that you can use an Ubuntu LiveCD to try and mount the partition or to fix it, but the tools available in linux for ntfs drives don't tend to work very well when the drives aren't working.  I think your best bet is to get help from windows users for now.
I will request that a moderator move this thread for you.

---

### Post by mariann53 on 2008-05-31
Thanx for the info i will try

---

### Post by Sef on 2008-05-31
Moved to Windows Discussions.

---

### Post by rickyjones on 2008-06-02
> **mariann53 said:**
> My slave drive volume disappeared after installing a new Windows Xp  SP2. I looked at disk management but i can only delete it nothing else. I use it for all my Media files 500GB. Can anyone help PLEASE

Is this volume a RAID array by any chance? Windows XP by default does not have drivers for most RAID controllers. If it is not RAID, is it SATA? Again, Windows may need the driver for the controller.

Thanks,
Richard

---

