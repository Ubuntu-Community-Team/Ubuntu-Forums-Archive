---
title: "When are we getting rounded corners?"
date: 2023-12-30
forum: Ubuntu, Linux and OS Chat
---

### Post by bkwjyk on 2023-12-30
Hi all, 

First time poster, medium-time user. It's industry standard now that all windows from all programs and apps have rounded corners. 
Why has this still not been implemented? 
I've been using since 22.04, and each time a new update is released I think "this is the one". Currently on the 24.04 dev build and still: sharp edges.
It makes the whole experience look very dated. Is this a GNOME problem?

---

### Post by SeijiSensei on 2023-12-30
There's an add-on for KDE Plasma that creates rounded corners.

[https://github.com/matinlotfali/KDE-Rounded-Corners](https://github.com/matinlotfali/KDE-Rounded-Corners)

Don't know anything about GNOME.

---

### Post by bkwjyk on 2023-12-31
> **SeijiSensei said:**
> There's an add-on for KDE Plasma that creates rounded corners.

[https://github.com/matinlotfali/KDE-Rounded-Corners](https://github.com/matinlotfali/KDE-Rounded-Corners)

Don't know anything about GNOME.

Thanks, there's one for GNOME too, but it hasn't been updated since GNOME ~42

---

### Post by Dennis N on 2023-12-31
Ubuntu 23.10 has rounded corners. Adwaita GTK4 apps have all 4 rounded, GTK3 has only top corners rounded. See attached image of a corner in Files.

---

### Post by bkwjyk on 2023-12-31
> **Dennis N said:**
> Ubuntu 23.10 has rounded corners. Adwaita GTK4 apps have all 4 rounded, GTK3 has only top corners rounded. See attached image of a corner in Files.

Yes... I am aware that some indeed are rounded. The inconsistency is the issue though.

---

### Post by werewulf75 on 2024-05-21
Bit of an old turkey this thread, but - really? Seems pretty lame to me to worry about rounded corners. Last time I looked, all my monitors/TVs were perfectly rectangular. Why waste screen estate with rounded corners?!

---

### Post by 909mjolnir on 2024-05-31
At least for XFCE4, you could install some extra window variants.  It took me a really long time to figure out it was this file installing the custom Appearance items for windows:  
Some of the variations mimic other operating systems.  It's nice.  Do 'sudo pacman -Ss ' and a keyword of what you're looking for (such as 'xfwm' without the quotes) and you'll get an explanation if it's found.  Good luck.  Personally, I prefer the square ones, but hate the "flat" themes.  

```

$ sudo pacman -Ss xfwm
...: 
extra/xfwm4 4.18.0-2 (xfce4)
    Xfce's window manager
extra/xfwm4-themes 4.10.0-5 (xfce4)
    A set of additional themes for the Xfce window manager

```

---

