---
title: "A two and a half year old problem still unresolved"
date: 2014-04-12
forum: The Cafe
---

### Post by SurfaceUnits on 2014-04-12
[h=1]"Enable mobile broadband" option gets unchecked[/h]
I could not configure nw-manager to autoconnect with mobile broadband.  I'm not sure if uncheking of "Enable mobile broadband" is the key issue  here, but after cheking "Enable mobile broadband", mobile broadband  starts connecting.


[https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/874900](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/874900)

Yes there are work arounds. So, given that there are work arounds, it should have been fixered.,.

---

### Post by buzzingrobot on 2014-04-12
Network manager, which has additional issues, is a Gnome effort, so if that bug is going to be fixed, it is going to be fixed upstream.

---

### Post by RichardET on 2014-04-13
I don't get the question. What do you mean by "Mobile Broadband"? If your wireless ethernet fails to connect,
Have you tried upgrading Ubuntu?

---

### Post by SurfaceUnits on 2014-04-13
14.04 updated every hour of the day

---

### Post by SurfaceUnits on 2014-04-13
<snip>

*Mobile broadband* is the marketing term for wireless Internet access through a portable modem, mobile phone, USB wireless modem,

---

### Post by chili555 on 2014-04-15
This is not the first, last or only bug that has been unfixed for 2 1/2 years. That's true of Linux, Windows and, if they were just a bit more forthcoming, OSX. I specifically said Linux and not Ubuntu because Network Manager, as has been pointed out, is part of Gnome. Gnome, Network Manager and this bug exist across most Linux distributions. Gnome, Network Manager and this bug are not an Ubuntu creation.

It is quite easy to decide that networking configuration ought to be handled in one nice neat GUI. It is quite another thing to get it working perfectly with all conceivable devices all the time and in any network environment. That last 2% or so must be just as difficult as the previous 98%!> Much of the issue comes from the fact that this particular device doesn't get powered on when connected; IIRC there has been some slight changes in powering methods for some devices, so maybe this got affected by these changes. I'm fairly confident that there is some finger-pointing going on here. NM says it's not their fault and the USB modem manufacturers either don't care about Linux or assert that NM is at fault.

If it were me, I'd institute the workaround and move on.

---

