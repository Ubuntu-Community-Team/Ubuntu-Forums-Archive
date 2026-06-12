---
title: "No gdm3 and no VTs. What now?"
date: 2018-09-04
forum: Ubuntu Development Version
---

### Post by Wise Ferret on 2018-09-04
I had troubles logging into gdm3 automatically, but I was able to bypass that by changing to a different VT {alt+f4) and changing back (alt+f1) or using startx. However, after last update, I cannot change my VT. Must I erase my installation completely now, or is there hope? Is there a new shortcut for changing VTs?

---

### Post by Wise Ferret on 2018-09-06
This seems to be [a well known bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1705369").
A workaround is there: in '/etc/gdm3/custom.conf' uncomment 
> #WaylandEnable=false
to
> WaylandEnable=false
And gdm3 works again.

---

