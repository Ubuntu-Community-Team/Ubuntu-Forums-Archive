---
title: "changing Gnome title bar"
date: 2009-09-21
forum: The Cafe
---

### Post by Marco A on 2009-09-21
.

---

### Post by Tibuda on 2009-09-21
Yes, but it is not very intuitive, because it is in a hidden config. Open the gnome configuration editor (it is hidden by default on the system menu, so use Alt+F2 > gconf-editor), and browse to /apps/metacity/general. Change the button_layout item to
```
close,maximize,minimize:menu
```
or something else you want.

---

### Post by Marco A on 2009-09-21
.

---

### Post by SunnyRabbiera on 2009-09-21
Alternately if you use emerald you can do this

---

