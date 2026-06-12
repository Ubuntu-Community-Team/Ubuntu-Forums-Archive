---
title: "Beta 2 live can't resize ext4 in gparted"
date: 2012-10-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pqwoerituytrueiwoq on 2012-10-02
i booted up my usb and tried to re-size my /home partition so i could make a 20gb one
every time i unmounted a partition another one would mount and when i got my /home unmounted  and tried to re-size it it failed to check the partition
i was able to resize it from my mint 13 usb without issue

---

### Post by dino99 on 2012-10-02
be sure to choose an unmounted partition, or an extended partition fully unmounted in case other inside partition is active.

---

### Post by jerrrys on 2012-10-02
Was it an extended partition?

bug #678831 which resolves a problem with overlapping partitions when resizing an extended partition

Seems to be fixed in 0.13

[http://distrowatch.com/?newsid=07336](http://distrowatch.com/?newsid=07336)

---

### Post by funicorn on 2012-10-02
I say LIVE CD is using your swap partition, which resides in the same extended partition as your /home does. So in gparted swapoff the swap partition first.

---

### Post by Elfy on 2012-10-02
I hope it is the swap, if it's what I've seen from time to time - it'll drive you mad.

Right click on a partition to unmount - gparted then refreshes and you'll spawn a bunch of thunar's as they all get mounted again. Right click on a partition to unmount ...

---

### Post by funicorn on 2012-10-02
It's the swap, or it's the ISO file itself. I hope the op is smarter than not seeing the latter possibility.

> **Elfy said:**
> I hope it is the swap, if it's what I've seen from time to time - it'll drive you mad.

Right click on a partition to unmount - gparted then refreshes and you'll spawn a bunch of thunar's as they all get mounted again. Right click on a partition to unmount ...

---

### Post by Elfy on 2012-10-02
I've had it here - not swap - not iso ;)

---

### Post by funicorn on 2012-10-02
Running in  live usb means no physical storage is used, except swap.

---

### Post by Elfy on 2012-10-02
I know exactly what it means.

That did not stop gparted mounting things and thunar opening ;)

---

### Post by pqwoerituytrueiwoq on 2012-10-02
for clarification it was a ext4 partition inside a extended partition
the ext4 was unmounted when i clicked apply in gparted

---

### Post by mc4man on 2012-10-02
Maybe this is somewhat related to the issues Xubuntu still seems to have with udisks2 & gvfs* (the doubling of internal volumes in thunar

/usr/sbin/gparted seems to have previously been used to inhibit automounting though possibly that was just for udisks & is no longer  a factor currently with udisks2. 
(gparted doesn't cause this in Ubuntu/unity, though does something else very wrong.

At least on the live session was a bit curious that when gparted starts & automounts all the dupes disappear from thunar, weird.

---

