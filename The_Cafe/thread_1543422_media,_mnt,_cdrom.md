---
title: "/media, /mnt, /cdrom"
date: 2010-08-01
forum: The Cafe
---

### Post by worksofcraft on 2010-08-01
I have these three different paths for mountable media... so I was reading some various old threads on the subject (oops soz accidentally replied on one) in the hope of gaining an understanding of exactly what the difference is...

I failed... can anyone help explain this for me please?

---

### Post by FuturePilot on 2010-08-01
[http://www.pathname.com/fhs/pub/fhs-2.3.html#MEDIAMOUNTPOINT]("http://www.pathname.com/fhs/pub/fhs-2.3.html#MEDIAMOUNTPOINT")

[https://www.redhat.com/archives/fedora-list/2004-November/msg03116.html]("https://www.redhat.com/archives/fedora-list/2004-November/msg03116.html")

---

### Post by worksofcraft on 2010-08-01
hum... thanks for those links :)

Looks like even the gurus are not convinced, but basically /cdrom and /mnt and /floppy are all anachronisms superseded my /media

I think I'll delete them... and see what happens ;)

---

### Post by CharlesA on 2010-08-01
Why even delete them when they aren't harming anything?

I've been using /cdrom/ as a temp mountpoint for media, since I don't need to type a long path out. Either that, or make my own mountpoints.

---

### Post by Barrucadu on 2010-08-01
From `man hier`:

```
/media This directory contains mount points for removable media such as CD and DVD disks or USB sticks.
...
/mnt   This directory is a mount point for a temporarily mounted file system.  In some distributions, /mnt contains subdirectories intended to be used as mount points for several temporary file systems.
```

I must admit, I've never heard of (or seen) /cdrom or /floppy in any distros before. Must be an Ubuntu (or Debian, maybe?) thing. However, /mnt definitely isn't superseded by /media, they serve different purposes.

---

### Post by conradin on 2010-08-01
Actually, you have nearly unlimited paths for mountable media, because you can make a directory and tell a folder or device to mount there. I think the only limit would be a limit on inodes, which is 4Million +? having 3 or 4 won't hurt anything. Deleting a mount point the system expects to find in the fstab or mtab can cause problems though. before deleting anything, you may want to check out what your fstab has for mount points.

---

### Post by szymon_g on 2010-08-01
hm... i saw /cdrom in freebsd; i've never saw it in linux (and i've never heard of /floppy).
i always use /mnt (for mounting windows partitions) and /media (for usbkeys, cds etc)

---

### Post by Åtta on 2010-08-01
I was asking myself pretty much the same thing a couple of days ago. Why have /media /mnt /cdrom etc. when they all do the same thing. Guess I've had my question answered now.

---

### Post by worksofcraft on 2010-08-01
> **CharlesA said:**
> Why even delete them when they aren't harming anything?


I find it confusing when there are many different places where things can get mounted automatically and I have to go looking for them.

Distinction between temporarily mounted distribution media and temporarily mounted file system is IMHO tenuous and serves little purpose.

... so I did check fstab as suggested and then deleted /mnt and /cdrom with apparent impunity :)

---

### Post by Elfy on 2010-08-01
I don't like having volumes on the desktop - I don't mind having usb's and cd's there as they are not permanently mounted. I mount my variosu data drives into /mnt so that I can leave nautilus showing the others on the desktop when they are there.

---

### Post by init1 on 2010-08-01
/media
When you insert removable media into your computer, Ubuntu will automatically mount it somewhere in /media.

/mnt
A traditional directory that many Unixes create. It's for mounting things that don't automatically get mounted. 

/cdrom
Symbolically linked to /media/cdrom

Basically, all three are just directories commonly used for mounting. You can mount something anywhere you want.

---

### Post by Paqman on 2010-08-01
In the default Gnome setup, the main practical difference between /mnt and /media is that stuff mounted in /media shows up on the desktop, and stuff in /mnt doesn't.

---

### Post by worksofcraft on 2010-08-02
> **Paqman said:**
> In the default Gnome setup, the main practical difference between /mnt and /media is that stuff mounted in /media shows up on the desktop, and stuff in /mnt doesn't.

I click "Places" and there amongst others, I see a drive named "Windows XP" - well I am sure you can guess what is on that drive... and it is also one of the options in my Grub boot menu btw.

Anyway, I click on it and sure enough it opens a file browser window and I can see all my Windows files there. It also puts a disk icon on my desktop named "Windows XP".

This is EXACTLY what I want: I can even right-click that and unmount it when I'm done :)

---

