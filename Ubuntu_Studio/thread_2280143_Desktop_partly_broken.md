---
title: "Desktop partly broken"
date: 2015-05-28
forum: Ubuntu Studio
---

### Post by burro on 2015-05-28
Hello,

For some time now my desktop has been completely free of items, except for the top and bottom panels. I'm also not able to set a desktop image, I see only the ubuntu-studio default. From an application, I can save a file to the Desktop, but it doesn't appear in the GUI. The files are however accessible via a terminal. If I log in as a different user everything works fine, so I must have a damaged config file somewhere but I don't know which. I did try reinstalling ubuntustudio-desktop once, but that didn't help.
Any suggestions please? 
Thanks

---

### Post by burro on 2015-05-28
Here's something strange: Reading a thread about a similar problem, it was recommended to visit /usr/share/applications with nautilus. I tried first visiting with the default ubuntu studio file browser - nothing happened. When I visited with nautilus the desktop files reappeared but the hard drive and rubbish bin didn't. When I log out and back in again the files (and also the wallpaper that I managed to reset) disappear, but, when I simply open nautilus, they reappear! Very odd. Does this mean anything to anyone?

---

### Post by sotiris2 on 2015-05-29
Is nautilus the default file manager in ubutu studio? Did you install any other file manager? If it wan't default did you install nautilus yourself?

---

### Post by burro on 2015-05-29
No, I installed nautilus later after the problem occurred. I remember some months ago, I absent mindedly reinstalled the ubuntu-desktop trying to fix the problem, so perhaps it came with that. Later though I reinstalled ubuntustudio desktop. I also tried uninstalling nautilus but reinstalled it - the desktop items only return if I launch nautilus - and as I said, the desktop is working fine for other users. I guess one solution would be to create a temporary user and transfer my files across, there must be a config file messed up somewhere.
Thanks,

---

### Post by Frogs Hair on 2015-05-29
In Ubuntu, Nautilus has the role of handling  the desktop including icons, background and decoration. Thunar in XFCE doesn't have the same role and this may be part of the problem. I've installed XFCE in Ubuntu in the past, but had keep Thunar as default in XFCE or I would end up with anomalies including context menu and background problems . Nautilus also brings a lot of Gnome dependencies with it.

---

