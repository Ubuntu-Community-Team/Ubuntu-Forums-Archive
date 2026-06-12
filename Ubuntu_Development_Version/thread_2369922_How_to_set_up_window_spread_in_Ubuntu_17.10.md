---
title: "How to set up window spread in Ubuntu 17.10"
date: 2017-08-28
forum: Ubuntu Development Version
---

### Post by geovino on 2017-08-28
How to set up window spread in Ubuntu 17.10?  is it still hot corners, since it's now gnome it should be working when mouse over upper left hand corner. Will it still do that?

---

### Post by mc4man on 2017-08-28
no such thing as "window spread" in gnome-shell. If you mean the activities overview then it's upper left corner.
However in a ubuntu session it's been disabled, re-enable with
```
gsettings set org.gnome.shell enable-hot-corners true
```

---

### Post by geovino on 2017-08-28
Thank you. Whatever you call it, having a hot corner to have all windows showing is very handy. That was a feature of Gnome that I liked :)

---

### Post by mc4man on 2017-08-28
> **geovino said:**
> Thank you. Whatever you call it, having a hot corner to have all windows showing is very handy. That was a feature of Gnome that I liked :)
Compiz did/does it better & has long before gnome-shell was around..

---

### Post by SunnyDaze on 2017-08-30
This is a Compiz feature.  You need to install **CompizConfig Settings Manager (CCSM)**.  

**sudo apt install compizconfig-settings-manager**

I personally set this feature, known as **Scale**, to mouse button 10, so I don't have to waste time dragging my mouse to a corner.

Once you have **CCSM** installed, go to the **Scale** plug-in, and then go to the **Bindings** tab.  There make sure the **Button Bindings Toggle Scale Mode** is checked, and then click the button to the right of the **Initiate Window Picker For All Windows** to set which mouse button, and/or keyboard combination, and/or windows edge initiates it.

---

### Post by joao.paris on 2018-01-10
> **SunnyDaze said:**
> This is a Compiz feature.  You need to install **CompizConfig Settings Manager (CCSM)**.  

**sudo apt install compizconfig-settings-manager**

I personally set this feature, known as **Scale**, to mouse button 10, so I don't have to waste time dragging my mouse to a corner.

Once you have **CCSM** installed, go to the **Scale** plug-in, and then go to the **Bindings** tab.  There make sure the **Button Bindings Toggle Scale Mode** is checked, and then click the button to the right of the **Initiate Window Picker For All Windows** to set which mouse button, and/or keyboard combination, and/or windows edge initiates it.


Is it possible to use CCSM on ubuntu 17.10 ? I have it installed but it doesn't do anything. I saw someone here saying it doesn't run in 17.10, so that's why i'm asking you how did you manage to do it.

ty in advance,

JP

---

### Post by howefield on 2018-01-10
Thread closed.

---

