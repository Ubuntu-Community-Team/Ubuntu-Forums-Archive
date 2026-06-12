---
title: "gnome-core startup?"
date: 2008-09-02
forum: Server Platforms
---

### Post by ajcurtis84 on 2008-09-02
Hello,

I have been looking at many postings trying to figure out how to install a minimum graphical environment on UBuntu server.

This computer is being configured as a VMware server but the configuration utility requires a graphical environment.

One posting that I saw said to install gnome-core. This installed fine and the VMware tools are happier *BUT* how do I start gnome? startx does not exist. There seems to be many things missing.

What do I need? How would I figure this out in the future?

TIA

- Allen

---

### Post by cariboo on 2008-09-02
You could install a minimal desktop like fluxbox or window maker.

Jim

---

### Post by Oldsoldier2003 on 2008-09-02
see [uhelp]community/ServerGUI[/uhelp]
```
sudo apt-get install xserver-xorg xserver-xorg-core
```
then install the lightweight WM of your choice.

---

### Post by ajcurtis84 on 2008-09-02
did you mean  xserver-xorg-core  ?

I can not find a x-window-core..

---

### Post by Oldsoldier2003 on 2008-09-02
> **ajcurtis84 said:**
> did you mean  xserver-xorg-core  ?

I can not find a x-window-core..

yeah I think I need to go back and redit that wiki page... thanks for pointing that out.

---

