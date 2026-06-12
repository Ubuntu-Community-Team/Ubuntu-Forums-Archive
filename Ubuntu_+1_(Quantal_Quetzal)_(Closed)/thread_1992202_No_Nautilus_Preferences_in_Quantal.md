---
title: "No Nautilus Preferences in Quantal"
date: 2012-05-31
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Yahoé on 2012-05-31
So there is no more Nautilus Preferences menu  in Quantal. There is a bug on this 999827.  Apparently (from the bug report) "These items were moved into an application menu, but it appears that  Unity is not correctly showing this menu with the normal menu"..."I am told indicator-application is responsible for this menu trickery.  Leaving the nautilus task open as it looks like a nautilus bug to users." This bug report is not being updated. Any idea how to activate the single click mouse behaviour in the meantime?


Regards?

---

### Post by mc4man on 2012-05-31
```
gsettings set  org.gnome.nautilus.preferences click-policy single
```
I'd suggest you install dconf-tools then open dconf-editor & have a look around

This setting is found from above commands path
org.gnome.nautilus.preferences

---

### Post by Yahoé on 2012-06-05
Thansk mc4man, that worked using dconfEditor, though there is still no "Preferences" menu in Nautilus.

---

### Post by jbicha on 2012-06-05
Alternatively, you could use GNOME Shell (or maybe GNOME Classic, I haven't tried) to get the other Nautilus app menu.

The bug will definitely be fixed before Ubuntu 12.10 is released.

---

### Post by philinux on 2012-06-06
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/999827](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/999827)

Changed in indicator-appmenu:
status: 	New &#8594; Confirmed
importance: 	Undecided &#8594; High

Thread marked as unsolved.

---

