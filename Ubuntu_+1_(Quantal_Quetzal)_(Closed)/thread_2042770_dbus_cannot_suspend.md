---
title: "dbus cannot suspend"
date: 2012-08-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by drou on 2012-08-15
Cannot suspend the machine... I close the lid and it simply locks the screen. the same happens when i select it from the menu. It seems like a dbus issue as the dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend has the same result. On the other hand pm-suspend works fine. Any ideas? i reintalled anything having to do dbus using synaptic

I 'm using gnome 3, but i don't think this has something to do

---

