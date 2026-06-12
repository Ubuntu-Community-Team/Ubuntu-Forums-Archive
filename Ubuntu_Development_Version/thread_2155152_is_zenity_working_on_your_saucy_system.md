---
title: "is zenity working on your saucy system ?"
date: 2013-06-17
forum: Ubuntu Development Version
---

### Post by dino99 on 2013-06-17
i only get a one line displayed into a very narrow scrolling box; for example when i want to choose something with winetricks.
It seems not having any dconf settings by the way to fix that.

---

### Post by vhaarr on 2013-06-18
> **dino99 said:**
> i only get a one line displayed into a very narrow scrolling box; for example when i want to choose something with winetricks.
It seems not having any dconf settings by the way to fix that.

You need to edit /usr/share/zenity/zenity.ui and add this on line 1024:

```
<property name="expand">True</property>
```

---

### Post by dino99 on 2013-06-18
> **vhaarr said:**
> You need to edit /usr/share/zenity/zenity.ui and add this on line 1024:

```
<property name="expand">True</property>
```

Many thanks  for that usefull tweak; now winetricks is displaying as expected.

[https://bugs.launchpad.net/ubuntu/+source/zenity/+bug/1192101](https://bugs.launchpad.net/ubuntu/+source/zenity/+bug/1192101)

---

