---
title: "Ubuntu Dock"
date: 2019-09-12
forum: Ubuntu Development Version
---

### Post by P-I H on 2019-09-12
There are problems with Ubuntu Dock
[https://bugs.launchpad.net/bugs/1843520](https://bugs.launchpad.net/bugs/1843520)

I haven't tried Dash to panel before, but it  works excellent. I use it in the bottom position.

---

### Post by PaulW2U on 2019-09-12
Yes, quite a few issues reported now:

[https://bugs.launchpad.net/bugs/1843419](https://bugs.launchpad.net/bugs/1843419) - 'Alt F2 + r' restart kills apps
[https://bugs.launchpad.net/bugs/1842910](https://bugs.launchpad.net/bugs/1842910) - right click menu appears wrong place
[https://bugs.launchpad.net/bugs/1843572](https://bugs.launchpad.net/bugs/1843572) - dock icons not functioning
[https://bugs.launchpad.net/bugs/1843605](https://bugs.launchpad.net/bugs/1843605) - frozen right click menu

Currently reported against gnome-shell. Most are probably related to the one that you referred to and hopefully will be fixed when an updated gnome-shell package arrives.

---

### Post by dino99 on 2019-09-12
About the 'right click' unexpected issue, i get a strange result when i copy/paste inside Calc : it create a gui object (white squared kind of table, which can be then resized by dragging) instead of pasting the previous copied cell. No idea if its a side effect of the reported bug above, but could be linked to the recent shell version.

---

