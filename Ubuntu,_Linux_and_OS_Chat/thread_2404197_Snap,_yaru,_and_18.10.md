---
title: "Snap, yaru, and 18.10"
date: 2018-10-21
forum: Ubuntu, Linux and OS Chat
---

### Post by aeronutt on 2018-10-21
In 18.10, it seems the default theme, yaru, is actually in a snap called "gtk-common-themes"?!

I'd prefer to remove snapd, and all other snaps because they are slow to very slow (even snap calculator takes 5 seconds to pop up, and I am dumbfounded by why snap creates ~/snap and not ~/.snap...anyway).

I searched to no success, but is there a way to load yaru in a more traditional way, without snaps?

---

### Post by Frogs Hair on 2018-10-21
Edit: Gtk themes common which includes icons is a snap application and It's  not available via apt as .deb from what I see. 

[https://github.com/ubuntu/yaru](https://github.com/ubuntu/yaru)

---

### Post by PaulW2U on 2018-10-21
> **aeronutt said:**
> I searched to no success, but is there a way to load yaru in a more traditional way, without snaps?
If you don't have the theme, install Tweaks:
```
sudo apt install gnome-tweaks
```
and select the theme from the Appearance tab. The Yaru theme should have been installed by default. The packages are:
```
yaru-theme-gnome-shell
yaru-theme-gtk
yaru-theme-icon
yaru-theme-sound
```

---

### Post by Frogs Hair on 2018-10-21
> without snaps? The OP is looking for a way to install the theme without using the provided sanp package.

Edit: Manual theme only installation is possible.  [https://www.gnome-look.org/p/1252100/](https://www.gnome-look.org/p/1252100/)

---

### Post by deadflowr on 2018-10-21
> The OP is looking for a way to install the theme without using the provided sanp package.

the yaru packages Paulw2u posted are all apt packages.

Edit:
> I'd prefer to remove snapd, and all other snaps because they are slow to very slow 
That's fine.
It won't harm or hurt the system.
I would suggest removing the snap packages first then remove the snapd package, so you don't have any leftover snap crud.
And then just delete the snap folder in Home.
> and I am dumbfounded by why snap creates ~/snap and not ~/.snap

The snap folder name's well established bug: [https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1575053]("https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1575053")

---

### Post by Frogs Hair on 2018-10-21
I think this is what the OP was writing about which is a snap though the yaru theme is available as .deb @ launchpad.

---

### Post by aeronutt on 2018-10-21
Yea, it's a bit confusing, all along with a mistake I made. So, here's how my 18.10 was configured.
Snap package "gtk-common-themes" was installed, which what I found included the Yaru theme. Oddly, all the yaru deb packages (gtk, icon, sound) were installed also (it turns out, when I looked for these debs before creating this post, I think I searched for yari, or such, so didn't see the debs. Ug.)

So, I deleted all the snap apps, then deleted snapd.

All is good with the universe . :)

Thanks for the quick responses and help!

---

### Post by deadflowr on 2018-10-22
gtk-common-themes includes common themes.
The purpose and usage is sort of described here: [https://forum.snapcraft.io/t/how-to-use-the-system-gtk-theme-via-the-gtk-common-themes-snap/6235]("https://forum.snapcraft.io/t/how-to-use-the-system-gtk-theme-via-the-gtk-common-themes-snap/6235")

---

### Post by aeronutt on 2018-10-22
> **deadflowr said:**
> gtk-common-themes includes common themes.
The purpose and usage is sort of described here: [https://forum.snapcraft.io/t/how-to-use-the-system-gtk-theme-via-the-gtk-common-themes-snap/6235]("https://forum.snapcraft.io/t/how-to-use-the-system-gtk-theme-via-the-gtk-common-themes-snap/6235")

I have no idea what all that means. :)

Seriously, one of my pet peeves with Ubuntu, Gnome, and Linux, is all the technical nomenclature used in describing the user interface, and the confusing architecture.

---

### Post by PaulW2U on 2018-11-03
> **aeronutt said:**
> Seriously, one of my pet peeves with Ubuntu, Gnome, and Linux, is all the technical nomenclature used in describing the user interface, and the confusing architecture.
Agreed, aeronutt.

A week or so after my posting in this thread I'm still not sure that what I posted was appropriate or if I even read the context of the thread correctly. I'm trying my best to understand snaps but as far as I am concerned my Ubuntu installations are built with **debs** and not **snaps**.

My reading of the [snapcraft]("https://forum.snapcraft.io/") forum suggests a very different future for Ubuntu compared to what many of us have been used to as the following are in existence or are being requested:

[LIST]
[*]Firefox snaps
[*]Chromium snaps
[*]Thunderbird snaps
[*]LibreOffice snaps
[*]snaps for frequently used applications
[/LIST]

---

### Post by maglin2 on 2018-11-04
For a while now I have been preferring snaps over .deb for Chromium and Firefox in the belief that sandboxing inherent in snaps provides an additional layer of security for these outward facing applications. 
I could easily be wrong. If so I would appreciate it if someone would let me know and I could save myself the bother.
They are a bit slower to load.

---

