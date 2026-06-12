---
title: "Which WM would use the least power?"
date: 2008-12-11
forum: The Cafe
---

### Post by Warpnow on 2008-12-11
Looking for a WM for my laptop, any suggestions? Want to keep the cpu inactive to save power and prolong battery life.

---

### Post by hessiess on 2008-12-11
Dwm?

---

### Post by -grubby on 2008-12-11
Twm?

---

### Post by p_quarles on 2008-12-11
Unless you are an exceedingly strange computer user, your applications are going to use far more watts than your window manager.

---

### Post by chucky chuckaluck on 2008-12-11
dwm and jwm are pretty light and useable. even openbox is pretty light, as is fluxbox. there must be a reason so many of the distros designed for old POS's use jwm.

---

### Post by Warpnow on 2008-12-11
> **p_quarles said:**
> Unless you are an exceedingly strange computer user, your applications are going to use far more watts than your window manager.

even sitting on my *** in class typing notes into mousepad?

---

### Post by mentallaxative on 2008-12-11
> **Warpnow said:**
> even sitting on my *** in class typing notes into mousepad?

If you're going to be doing that, scrap X and mousepad altogether and type in your notes with nano. The black screen probably uses less energy and you don't have to think about window managers.

---

### Post by p_quarles on 2008-12-11
> **Warpnow said:**
> even sitting on my *** in class typing notes into mousepad?
On my system, the window manager (Fluxbox) averages less CPU time than than the terminal emulator I use (urxvt), among other things. Ultimately, the choice to run X makes the window management options all pretty much the equivalent of one another.

---

### Post by Warpnow on 2008-12-11
> **mentallaxative said:**
> If you're going to be doing that, scrap X and mousepad altogether and type in your notes with nano. The black screen probably uses less energy and you don't have to think about window managers.

I'd like to do that but I'm afraid the newbishness will kill me. Is there a way I can do a full install but only boot the bare necessities? Like a boot option for it?

Also, anyone know how to check the battery from the command line?

---

### Post by kerry_s on 2008-12-11
> **Warpnow said:**
> I'd like to do that but I'm afraid the newbishness will kill me. Is there a way I can do a full install but only boot the bare necessities? Like a boot option for it?

Also, anyone know how to check the battery from the command line?

you can use the fail safe session from the gdm menu, that will just give you a xterm, which you can use to start your note taking program. it should use less power since there won't be anything else running, xorg is still the most cpu usage program, if you want less cpu usage, killing X and using the console is the best.

**cat /proc/acpi/battery/BAT1/?**
you'll have to look what the file is called, i don't have any battery's for this 10 year old laptop.

---

### Post by Heinzelotto on 2008-12-11
> **Warpnow said:**
> 
Also, anyone know how to check the battery from the command line?

try "acpi" ;)

---

### Post by chucky chuckaluck on 2008-12-11
this thread is making me want to reinstall kde4, again, and use nothing but terminal apps.

---

### Post by billgoldberg on 2008-12-11
> **Warpnow said:**
> Looking for a WM for my laptop, any suggestions? Want to keep the cpu inactive to save power and prolong battery life.

Well, to start with dump gnome and all the apps it comes with.

Install a cli ubuntu install.

Install fluxbox with light-weight apps.

I'm thinking pcmanfm as file manager, epiphany as browser, xmms as music player, ...

---

