---
title: "Quantal will not allow safe removal of USB drive"
date: 2012-06-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-06-04
For a few days now (and since problems with .isos and SDC in another forum) QQ will not safely remove USB drives.

---

### Post by wilee-nilee on 2012-06-04
> **ventrical said:**
> For a few days now (and since problems with .isos and SDC in another forum) QQ will not safely remove USB drives.

What happens if you hit eject, I noticed this at times, some time it has the safe removal some times it does not. 

Eject works fine.

---

### Post by ventrical on 2012-06-04
> **wilee-nilee said:**
> What happens if you hit eject, I noticed this at times, some time it has the safe removal some times it does not. 

Eject works fine.

  It ejects just fine .. but I am wondering if this is a problem with freshly installed .iso's onto USB sticks. Something doesn't seem right here.

---

### Post by wilee-nilee on 2012-06-04
> **ventrical said:**
> It ejects just fine .. but I am wondering if this is a problem with freshly installed .iso's onto USB sticks. Something doesn't seem right here.

Missing on the full install as well at times.

---

### Post by nll on 2012-06-04
Well, eject and safely remove are the same option, so it makes sense to remove one. Eject is nicer because it gives a notification and fixes [this 5-years old bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/85961"). So we are not losing anything.

---

### Post by mc4man on 2012-06-04
Mentioned some of this here
[http://ubuntuforums.org/showthread.php?t=1996466](http://ubuntuforums.org/showthread.php?t=1996466)

Basically with the new gvfs & udisks2 there is no Safely remove seen here anymore, not with flash drives or usb hdd drives 
(see Safely remove  as  eject, power down or the other way around, don't know, don't care, result is device is ejected & powered down

Additionally some flash drives only get an unmount option option, others get an eject only option, usb hdd drives only an unmount 
(as seen here with 9 flash, 3 hdd

---

### Post by ventrical on 2012-06-04
Thanks mac4man. Yes, I seen your thread.

That explains that then. :)

---

