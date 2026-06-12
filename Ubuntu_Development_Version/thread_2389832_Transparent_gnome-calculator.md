---
title: "Transparent gnome-calculator"
date: 2018-04-22
forum: Ubuntu Development Version
---

### Post by P-I H on 2018-04-22
Bionic Beaver is working quite OK and the new Communitheme looks great. There are however some problems as this with a transparent Calculator.

---

### Post by mc4man on 2018-04-22
Well that theme is a wip &  not totally ready. As far as gnome-calculator the default is a snap version which won't work well yet with the community theme
Run this & you'll likely see issue
```
snap run gnome-calculator
```

If you install the .deb version of gnome-calculator it should be ok with the community theme

---

### Post by pqwoerituytrueiwoq on 2018-04-22
looks like you do not have read permissions on the file on that error message, you should have read access and root should have write access to that file

---

### Post by mc4man on 2018-04-22
I guess you could remove the gnome-calculator snap, then re-install with the --classic option. Probably would then work ok  with community theme.
( or try ppa version of theme if using the snap version of theme.

Likely better to mention here or inquire as to where to make issues with snaps (I'd gather Canonical supported snaps can be filed on launchpad...
[https://community.ubuntu.com/t/snapping-communitheme/4890](https://community.ubuntu.com/t/snapping-communitheme/4890)  # seems to now be read only..
or
[https://forum.snapcraft.io/](https://forum.snapcraft.io/)

---

### Post by mc4man on 2018-04-22
Actually none of the current default installed snaps will work with the snap community theme properly...

---

### Post by P-I H on 2018-04-23
I will use Tweaks to change the applications theme to Ambiance for now and wait for an update.
However in my view the Communitheme looks better.

---

