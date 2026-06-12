---
title: "HOWTO Kiosk OPAC station with Xubuntu BETA RELEASE"
date: 2013-01-20
forum: Security
---

### Post by Charles-2007 on 2013-01-20
I have attached a write-up of how I created a KIOSK using Kubuntu 12.04 with its native XFCE 4.8.  Please consider this a "beta" as I am still doing some testing.  I would appreciate your feedback.

The objective is a box dedicated to a specific purpose that can sit more-or-less unattended.

---

### Post by Charles-2007 on 2013-02-06
UPDATED.  Check under my userID or here:

[http://ubuntuforums.org/showthread.php?t=2113023](http://ubuntuforums.org/showthread.php?t=2113023)

Way easier to lock down the Chromium browser.

---

### Post by bodhi.zazen on 2013-02-06
Nice work, but why not work with existing projects?

Ubuntu has a guest session as does Fedora.

In addition there are entire distros devoted to kiosk mode.

---

### Post by Charles-2007 on 2013-05-27
The parameters with the Guest Session seem the same in the different Linux distributions (I tried them).  On logout the system does wipe any changes the guest makes, but it is pretty difficult to lock down what a guest can do.  Guest Session seems intended to let the user do whatever he/she wants without impacting the next user -- not really restricting what the user can do.  Depends on the objective (mine is limited access).  Yes there are also some kiosk distributions out there -- either non-free or dated (I tried many of them too).  The most updated one appears to be Linutop (nonfree) which appears to be basically what I did.  I also wanted to do something that would run on creaky old machines.

---

