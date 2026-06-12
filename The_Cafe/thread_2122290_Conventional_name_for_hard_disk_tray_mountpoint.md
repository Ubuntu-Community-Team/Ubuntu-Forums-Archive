---
title: "Conventional name for hard disk tray mountpoint?"
date: 2013-03-04
forum: The Cafe
---

### Post by stlu on 2013-03-04
Hi,

I have a USB drive on /mnt.  I want to mount a hard drive in a removable tray enclosure, and stupid me will get confused if I create /mnt2 at root level.  Is there a conventional mountpoint for a cold-swap hd tray?  I'd like to adopt from existing conventions.  If nobody knows of such, I'll make up my own, probably /hdtray.

thx,

---

### Post by The Cog on 2013-03-04
I think the normal thing to do is to use directories under /mnt, e.g. /mnt/stick, /mnt/hdtray, /mnt/backup. Or for removable media, it normally gets auto-mounted under /media/username/volumename.

---

### Post by tgalati4 on 2013-03-04
I prefer to let the operating system create and maintain the mount point.  This way it works in all applications.  If you create your own mount point, then you will have to hunt for the drive every time you want to open a file in an application.

For what gets mounted, in a terminal:

```
sudo fdisk -l
mount -l
```

To change the mounting rules, including the name and location of the mount point, you could change the udev rules.  But you will have to search  for a tutorial on how to do it, since it's not trivial.

---

### Post by stlu on 2013-03-05
> **The Cog said:**
> I think the normal thing to do is to use directories under /mnt, e.g. /mnt/stick, /mnt/hdtray, /mnt/backup. Or for removable media, it normally gets auto-mounted under /media/username/volumename.


I like this.  /mnt is what I used for manual mounting, and /mnt/hdtray is less likely to trip me up then /mnt2 or some such name.  I will just have to get into the habit of always using a subfolder under /mnt so I don't block the subfolder by mounting another filesystem on /mnt accidentally...  And thanks!

I am happy with the way my USB drives are auto-mounted under /media, so I intend to leave that system alone.

> **tgalati4 said:**
> I prefer to let the operating system create and maintain the mount point.  This way it works in all applications.  If you create your own mount point, then you will have to hunt for the drive every time you want to open a file in an application.

For what gets mounted, in a terminal:

```
sudo fdisk -l
mount -l
```

To change the mounting rules, including the name and location of the mount point, you could change the udev rules.  But you will have to search  for a tutorial on how to do it, since it's not trivial.


I don't want to do this, because the hard drives are changing, sometimes unformatted, sometimes with differenct layouts (Such as Slackware which assigns the first partition as swap)  With a variety of possibilities I need to call the mount command manually.

---

### Post by ssam on 2013-03-06
According to the standard /media is the place to mount removable drives.
[http://www.pathname.com/fhs/pub/fhs-2.3.html#MEDIAMOUNTPOINT](http://www.pathname.com/fhs/pub/fhs-2.3.html#MEDIAMOUNTPOINT)
/mnt is for when you want to do a temporary one off mount of something. (but historically some linux distros would automount devices under /mnt)

---

