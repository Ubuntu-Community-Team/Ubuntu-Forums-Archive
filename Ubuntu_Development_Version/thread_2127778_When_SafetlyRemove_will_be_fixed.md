---
title: "When SafetlyRemove will be fixed?"
date: 2013-03-21
forum: Ubuntu Development Version
---

### Post by forcecore on 2013-03-21
It is highly critical to me, any ideas when fix will land?

---

### Post by zika on 2013-03-21
> **forcecore said:**
> It is highly critical to me, any ideas when fix will land?Any bug-report on LaunchPad?

---

### Post by ronacc on 2013-03-21
If you are referring to things remounting as soon as "safely removed"  I bugged that a couple of years ago , I can't find the bug right now but I think it still open because I still get notifications on it . Just use eject , that don't remount .

---

### Post by cariboo on 2013-03-21
Eject works well for me.

---

### Post by ronacc on 2013-03-21
found the bug ,  I filed it back in july 2010  ,it is confirmed and has many subscribers but is stll of "undecided" importance and still " unassigned" it is bug # 608508 if you want to add yourself to the list .

---

### Post by forcecore on 2013-03-21
Ubuntu 12.04 can power off devices but now 13.04 is like Win 7 that too cannot power down devices, only remove.

---

### Post by mc4man on 2013-03-21
Don't think there is a wide enough use case to bring back safelyremove 
For myself the only time really useful was when I had a desktop with external usb(s) that did not have their own power off switch. So sometimes when done with the drive or not intending to use that session would use safelyremove to power off without having to pull the usb cable or power connector.

You can do yourself -  blue to suit
```
udisks --unmount /dev/[COLOR="#0000CD"]sdb1[/COLOR] && udisks --detach /dev/[COLOR="#0000CD"]sdb[/COLOR]
```

---

### Post by mc4man on 2013-03-21
Though something I've not seen lately a new flash drive I just picked up gets a "Safely remove" option both in nautilus & from the unity launcher
(not that there is any value there per se.

edit: all my usb drives that are of a certain type do get a Safely remove option, others don't 
(ones that get the icon shown in screen get, those that get a usb flash drive option don't 
Will have to pickup my usb external drives & see what they get,  I'd suspect they get the Sr option also

---

### Post by mc4man on 2013-03-27
This was fixed here to some extent, most hot-plugged devices will get a safely remove option (at least as far as usb flash & hdd's
Some flash drives will not & as far as usb hdd's may depend on whether connected (or powered on) at boot or after
[https://bugs.launchpad.net/ubuntu/+source/udisks2/+bug/1067876](https://bugs.launchpad.net/ubuntu/+source/udisks2/+bug/1067876)

---

### Post by rrnbtter on 2013-03-27
Greetings,
I right click my usb in nautilus and choose "eject" and I get a safe remove process. Also, with today's updates and Kernel 3.9RC4 every problem I can think that I've had has been fixed. It could change in the next 10 minutes but right now I'm happy.

---

