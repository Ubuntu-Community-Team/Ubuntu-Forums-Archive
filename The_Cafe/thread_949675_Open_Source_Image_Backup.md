---
title: "Open Source Image Backup"
date: 2008-10-16
forum: The Cafe
---

### Post by StitchJAcket on 2008-10-16
Okay so had a rather interesting question asked the other day. Well let me start from the begining. I work at this company blah blah we config about 25,000 units a year (rough estimate) and we use Ghost to deploy our images. So my manager asks can we use acronis. My response of course was yeah it will be cheaper but there has to be a way to do this without having to pay super high licensing fees. So myu question to this great ubuntu community is. What kind of open source imaging clients are out there and are the capable of doing multicasts (it's a nice feature and saves loads of time):popcorn:

---

### Post by fiddledd on 2008-10-16
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by StitchJAcket on 2008-10-16
> **fiddledd said:**
> [http://clonezilla.org/](http://clonezilla.org/)

Thanks I'll check it out.

---

### Post by zmjjmz on 2008-10-16
If you get a lot of the same computers you can _very easily_ use dd to get those images in.
You'd need a LiveCD to do it (Ubuntu is good, it works for me) and a portable USB harddrive.
What you do is you take a fresh install of whatever OS it is on a computer, reboot into a LiveCD, -**DO NOT MOUNT THE INTERNAL HARD DRIVE**-, and then issue (in  a terminal) ```
dd if=/dev/sda of=/mnt/sdb1/Images/image.img
```
Obviously /dev/sda corresponds to whatever your hard drive is, and /mnt/sdb1 is the [mounted] portable hard drive.
DO NOT MIX THOSE UP
So when you need to copy the image to a new computer, you would take a LiveCD again, and do this
```
dd if=/dev/sdb1/Images/image.img of=/dev/sda
```.
Obviously you should use the internal hard drive as /dev/sda and the portable drive with the image on it as /mnt/sdb1/Images/image.img.
Of course you might want to watch out as doing this with a proprietary system is usually a copyright violation or something

I suppose clonezilla is easier, but this is what worked for me.

---

### Post by stinger30au on 2008-10-16
[this livecd may interest you, its called restore]("http://restore-backup.com/index.php?option=com_docman&task=cat_view&gid=34&Itemid=1")

---

