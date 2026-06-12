---
title: "gtk-3.10, maybe some bugs, ect."
date: 2013-12-10
forum: Ubuntu Development Version
---

### Post by mc4man on 2013-12-10
14.04 will go to 3.10, was tested for  a while in the Desktop ppa & now is in -proposed
Some issues have already been fixed, some not.
If any are found certainly worth filing a bug on promptly.

The one that I currently find to be a real  pita is that with 3.10 synaptic will always return to the top of a scrollable window after any action on a package. 
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1259725](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1259725)

---

### Post by ventrical on 2013-12-10
Thanks for heads up ! :) lol

---

### Post by mc4man on 2013-12-10
One little change that I don't believe is a bug but took a few to get used to  - 
when dragging an object you no longer see the object, just the little hand+ cursor
I think I like it better than older method, more precise, especially with nautilus's auto open a dir. on DnD
(I find the auto open on hover useful & also quite annoying so here have disabled it in icon view but left enabled for  breadcrumbs, listtree & sidebar

---

### Post by philinux on 2013-12-11
Here's some background.
[http://www.webupd8.org/2013/12/gtk-310-lands-in-ubuntu-1404-trusty-tahr.html](http://www.webupd8.org/2013/12/gtk-310-lands-in-ubuntu-1404-trusty-tahr.html)

---

### Post by mc4man on 2013-12-11
A testing ppa for u-c-c has been here though it may start to get outdated packages
[https://launchpad.net/~ubuntu-desktop/+archive/unity-control-center](https://launchpad.net/~ubuntu-desktop/+archive/unity-control-center)
haven't seen much issue here other than it feels some panels open a little slower

May be good to note that u-c-c conflicts with g-c-c so while unity & gnome-shell can both be installed,  with u-c-c there will be no settings available in a gnome-shell session
(at least for the moment thru the normal method

Edit: it appears the intention is both control-center packages can be installed, just not possible right now.

---

### Post by mc4man on 2014-03-23
> **mc4man said:**
> 
The one that I currently find to be a real  pita is that with 3.10 synaptic will always return to the top of a scrollable window after any action on a package. 
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1259725](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1259725)
After several months this has been fixed in new synaptic, atm not available in Ubuntu, hopefully shortly
(tested here, works fine

---

