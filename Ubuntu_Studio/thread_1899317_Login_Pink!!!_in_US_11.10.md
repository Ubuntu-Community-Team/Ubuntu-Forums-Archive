---
title: "Login Pink!!! in US 11.10"
date: 2011-12-23
forum: Ubuntu Studio
---

### Post by royleith on 2011-12-23
You might think this is a trivial problem, but it is starting to make me crazy. XFCE has fewer GUI editors and the problem I have is with the login screen.

It is a violent colour of pink.

I tried editing /etc/X11/app-defaults/Bitmap-color, but it had no effect. I have restored the original file, just in case.

Ubuntu Studio 11.10 seems to be working well, atm, but I am just about to install it on a laptop that uses a Firewire audio interface and so my assessment may be premature.

I have found how to do much of what I need in XFCE and I am hoping it has less overheads than the latest Gnome. That pink login screen has got to go, though!

Regards
Roy Leith

---

### Post by jejeman on 2011-12-23
Open
/etc/lightdm/lightdm-gtk-greeter.conf
and change the backgorund.

---

### Post by Elfy on 2011-12-23
I had similar prior to installing the nvidia driver from additional drivers.

---

