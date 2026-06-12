---
title: "gnome-control-center default size"
date: 2017-10-07
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-10-07
Here the g-c-c opens @ Height: 755 which is about 28px too small to show all the panels. Seems silly to always exclude the last panel from the default view.
scr1 default, scr.2 what should be the default

---

### Post by amano on 2017-10-08
Well, confirmed. Really annoying.

---

### Post by mc4man on 2017-10-08
filed
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1722079](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1722079)

---

### Post by Chanath on 2017-10-08
> **mc4man said:**
> Here the g-c-c opens @ Height: 755 which is about 28px too small to show all the panels. Seems silly to always exclude the last panel from the default view.
scr1 default, scr.2 what should be the default

The standard laptop height is 768 pix, so to show all the panels, you need to hide the top panel. The default Ubuntu comes with a fixed top panel. Most probably the idea is that a user would look in Settings only once, or max 2-3 times.

---

### Post by mc4man on 2017-10-08
> **Chanath said:**
> The standard laptop height is 768 pix, so to show all the panels, you need to hide the top panel. The default Ubuntu comes with a fixed top panel. Most probably the idea is that a user would look in Settings only once, or max 2-3 times.
That does make sense about the most common rez..

---

### Post by mc4man on 2017-10-14
Solved as now getting proper default window size, i.e.
Width: 1054
Height: 784

---

