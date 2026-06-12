---
title: "Gnome Terminal Transparency is Broken"
date: 2017-06-02
forum: Ubuntu Development Version
---

### Post by joseph592 on 2017-06-02
I upgraded from 17.04 to 17.10 dev, Gnome Shell 3.24.2, the transparency feature in terminal is not working. When you enable it a large white border surrounds the terminal window and the window is transparent. Uncheck transparency and white border is gone the window then goes to a black background. The ability to edit a profile is hit and miss, at times when you try to edit a profile the window just crashes. I submitted a bug report for this. I tested this both in gnome wayland and gnome xserver. Anyone else noticed this?

Regards

Edit : I just installed Gnome, am running Gnome Classic and terminal transparency is unaffected. Terminal seems to be ok in pure Gnome.

---

### Post by cariboo on 2017-06-03
Works fine here on upgraded from 17.04 to 17.10 Ubuntu-Gnome

**Edit:** it seems it doesn't show in the screenshot though. A shot of the whole screen does show the transparency

---

### Post by jbicha on 2017-06-03
My understanding is that this issue only affected GNOME on Wayland, not sessions that don't use Wayland.

---

### Post by joseph592 on 2017-06-06
You're correct it is only on Gnome Wayland. My mistake.

---

### Post by jbicha on 2017-06-06
[LP: #1650395]("https://launchpad.net/bugs/1650395")

---

