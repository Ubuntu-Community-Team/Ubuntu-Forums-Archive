---
title: "Compiz on Gnome-Shell?"
date: 2011-08-09
forum: The Cafe
---

### Post by danyc05 on 2011-08-09
Will compiz effects work on gnome-shell? For example:cube, wobbly windows, etc.

---

### Post by kaldor on 2011-08-09
Compiz is not compatible with GNOME Shell as of yet.

---

### Post by danyc05 on 2011-08-09
alright thanks

---

### Post by Inodoro Pereyra on 2011-08-10
> **kaldor said:**
> Compiz is not compatible with GNOME Shell as of yet.

What do you mean? I have always used Gnome (it's what comes standard with Ubuntu, right?:confused:) and have used Compiz and all the animations without a problem...

---

### Post by cariboo on 2011-08-10
Gnome-shell uses mutter as a windows manager, compiz is a compositing windows manager. You can't use two windows managers at once.

---

### Post by kaldor on 2011-08-10
> **Inodoro Pereyra said:**
> What do you mean? I have always used Gnome (it's what comes standard with Ubuntu, right?:confused:) and have used Compiz and all the animations without a problem...

GNOME Shell is the new Desktop Environment featured in GNOME 3. Ubuntu is using GNOME 2.32 with Unity.

---

### Post by TheNosh on 2011-08-10
> **Inodoro Pereyra said:**
> What do you mean? I have always used Gnome (it's what comes standard with Ubuntu, right?:confused:) and have used Compiz and all the animations without a problem...

Gnome 3 has some major changes to the interface. The new shell interface does not work with Compiz.

---

### Post by NightwishFan on 2011-08-10
Can the fallback mode work with Compiz?

---

### Post by 3Miro on 2011-08-10
Gnome 3 does work with Compiz. Unity is Compiz and 11.10 does come with Gnome 3 + Unity.

Gnome-shell is the default Gnome 3 Windows Manager and User Interface. Compiz does not work with Gnome-shell, that is, if you want Gnome-shell UI then you cannot get compiz effects.

---

### Post by u-noob-tu on 2011-08-10
What about a compiz-like window manager for GNOME-Shell? I mean, a window manager for GNOME-Shell that has compiz-like functionality. Is there one in development?

---

### Post by Inodoro Pereyra on 2011-08-10
> **kaldor said:**
> GNOME Shell is the new Desktop Environment featured in GNOME 3. Ubuntu is using GNOME 2.32 with Unity.

> **TheNosh said:**
> Gnome 3 has some major changes to the interface. The new shell interface does not work with Compiz.


Didn't know that.:oops: Thank you.

---

### Post by 3Miro on 2011-08-10
> **u-noob-tu said:**
> What about a compiz-like window manager for GNOME-Shell? I mean, a window manager for GNOME-Shell that has compiz-like functionality. Is there one in development?

Gnome-shell is the windows manager. If you want fancy effects with Gnome-shell, they will have to be implemented as part of Gnome-shell. I think they will eventually add more effects, but I don't think they are working on this right now.

---

### Post by NightwishFan on 2011-08-10
> **u-noob-tu said:**
> What about a compiz-like window manager for GNOME-Shell? I mean, a window manager for GNOME-Shell that has compiz-like functionality. Is there one in development?

The gnome shell acts a plugin for Gnome 3's window manager (which is named Mutter). So if you replace mutter you also lose the gnome shell. Mutter itself already supports compositing and animations so I am sure it could be extended to do more effects if desired. Perhaps the extension system to the shell could amount to this as well. So far I am quite sure it does not and is probably not planned.

I was wondering if anyone has a system with Gnome 3 installed (i do not at the moment) if you can replace with compiz while running in fallback mode. Logically I would think you could.

---

