---
title: "gdm doesn't load anymore"
date: 2012-09-21
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by geolab on 2012-09-21
Hi. with latest updates (I'm using the gnome ubuntu flavour) I have the boot process ending with a black screen and the mouse cursor. no gdm is loaded. I have to switch to console and log in then start x.
my video card is a ati radeon 7500m 
I tried to reinstall gdm but no luck
what can I try? is it a problem of ati driver or gdm?

---

### Post by Deepak A on 2012-09-21
Put *startx* in some startup file.

---

### Post by RavisPohan on 2012-09-21
I had the same problem. Purging and reinstalling GDM seemed to fix it, although it is still more sluggish than usual.

EDIT: Nah, it's fine. Just the first login was a bit slower.

---

### Post by geolab on 2012-09-21
i switch to text console, login and then i give the startx comand.
but it worked untill a week ago.. I wonder if somebody else has the same problem and how to report it

---

### Post by dino99 on 2012-09-21
open synaptic:
- purge gdm & lightdm installed packages
- then reinstall them both, and set lightdm as default

its working here on i386

):P

---

### Post by zika on 2012-09-21
> **dino99 said:**
> open synaptic:
- purge gdm & lightdm installed packages
- then reinstall them both, and set lightdm as default

its working here on i386

):PLightDM might have some packages depending on it so be carefull ... ):P

---

### Post by lolpenguin on 2012-09-22
No, no, no!

GNOME Shell (3.5.x) won't run if you aren't using GDM! If it does, then many features are disabled/broken.

---

### Post by jbicha on 2012-09-22
> **lolpenguin said:**
> No, no, no!

GNOME Shell (3.5.x) won't run if you aren't using GDM! If it does, then many features are disabled/broken.

Not really, this was fixed in gnome-shell 3.5.92. You still need to have GDM installed but you can still use LightDM as your login screen. The difference is that you're use gnome-screensaver instead of the fancy looking new lock screen when you lock your computer.

If you still have problems with using LightDM, please open a bug (especially since I'm basically only using gdm).

---

