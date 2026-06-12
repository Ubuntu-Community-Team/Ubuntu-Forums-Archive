---
title: "Grub 2 cursor never leaves the screen"
date: 2012-02-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by pqwoerituytrueiwoq on 2012-02-18
i just downloaded the daily copy of 12.04 64bit 
i made my usb boot it i hear the login prompt sound and the grub 2 cursor is still blinking on my screen
i have a nvidia GPU
ctrl+alt+f1 did nothing

i have had issues with grub 2 on this rig before (no boot menu ever shows up)

anyone know have a suggestion?

---

### Post by cariboo on 2012-02-18
HAve you tried starting with nomodeset enabled? Press any key at the initial boot screen to see the menus, then press F5 and enable nomodeset, then continue on.

---

### Post by kansasnoob on 2012-02-19
> **pqwoerituytrueiwoq said:**
> i just downloaded the daily copy of 12.04 64bit 
i made my usb boot it i hear the login prompt sound and the grub 2 cursor is still blinking on my screen
i have a nvidia GPU
ctrl+alt+f1 did nothing

i have had issues with grub 2 on this rig before (no boot menu ever shows up)

anyone know have a suggestion?

Something you might try:

[http://ubuntuforums.org/showpost.php?p=11580249&postcount=2](http://ubuntuforums.org/showpost.php?p=11580249&postcount=2)

---

### Post by pqwoerituytrueiwoq on 2012-02-19
> **cariboo907 said:**
> HAve you tried starting with nomodeset enabled? Press any key at the initial boot screen to see the menus, then press F5 and enable nomodeset, then continue on.
worked like a charm, thanks

@kansasnoob, i would have but i could not get a GUI/TTY to work from

---

