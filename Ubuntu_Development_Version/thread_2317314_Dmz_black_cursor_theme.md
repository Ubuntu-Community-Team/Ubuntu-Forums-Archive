---
title: "Dmz black cursor theme"
date: 2016-03-15
forum: Ubuntu Development Version
---

### Post by GreatDanton on 2016-03-15
I noticed that changing mouse cursor theme from Dmz to Dmz black in mouse and touchpad menu [xubuntu], doesn't work after restart. In firefox cursor is black, if I hover over desktop background it's still white.

[ATTACH=CONFIG]267824[/ATTACH][ATTACH=CONFIG]267823[/ATTACH]

---

### Post by Dennis N on 2016-03-15
For complete cursor change, the Mouse and Touchpad dialog is not enough. The default cursor is still DMZ-white. You also need to change that to DMZ-black with:

[FONT=Courier New]sudo update-alternatives --config x-cursor-theme[/FONT]

and read the directions it gives.

---

### Post by GreatDanton on 2016-03-19
> **Dennis N said:**
> For complete cursor change, the Mouse and Touchpad dialog is not enough. The default cursor is still DMZ-white. You also need to change that to DMZ-black with:

[FONT=Courier New]sudo update-alternatives --config x-cursor-theme[/FONT]

and read the directions it gives.

Thanks that solved this. Shouldn't be this problem reported as a bug?

---

### Post by pqwoerituytrueiwoq on 2016-03-19
given this bug has been around for at least a decade now i'm sure there is a report somewhere (probably several)

---

### Post by motang on 2016-03-21
Annoying that it has been fixed yet. Very old bug and annoying one at that.

---

