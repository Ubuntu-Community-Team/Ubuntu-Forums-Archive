---
title: "virtualbox-ose-modules-generic update can not be checked off in Update Manager"
date: 2008-08-06
forum: Virtualisation
---

### Post by diablo75 on 2008-08-06
There was an update that appeared in Update Manager a couple of days ago that I can't get checked off.  Virtualbox continues to run, despite the fact that I can't download that update.  I was just wondering, why can't that update be selected?  What can I do to take care of this?

---

### Post by YokoZar on 2008-08-07
It seems that the update is for a newer series of kernel modules for a kernel that isn't actually in Hardy (-20).  My guess is there was a new proposed kernel that didn't get merged into -updates due to some problem, but for some reason virtualbox-ose-modules did.

---

### Post by diablo75 on 2008-08-07
Compared to the experience I had while using VMware Server, I find this to be very impressive (if I'm understanding this correctly).  An update has been issued BEFORE a kernel update came down the wire.  (GASP!!!!)  I mean... F-ing WOW!  In any event, I know how to very easily recompile the kernel headers, so it doesn't worry me... but that the developers actually went out of their way to issue an update in advanced...
:guitar:

---

### Post by REy_ on 2008-08-07
That's because SUN now owns this product and they are on the ball. You know I've used Both VMWareServer0 and Virtualbox and for preformance and stability Vbox takes the cake.

---

