---
title: "Ubuntu 10.04 Server booting into Gui, why?"
date: 2013-01-05
forum: Server Platforms
---

### Post by sentinelace on 2013-01-05
AFter upgrade my server boots the the gui.  I want it to boot to terminal like it used to.  I removed desktop and gnome and yet it still tries but now I get "low graphic" error.  Why would it need graphics to boot to terminal?

---

### Post by lykwydchykyn on 2013-01-05
you probably need to uninstall gdm.

---

### Post by sentinelace on 2013-01-05
what is the best way?   if I install gdm will I not get the low graphics error?

---

### Post by sandyd on 2013-01-05
> **sentinelace said:**
> what is the best way?   if I install gdm will I not get the low graphics error?

GDM stands for Gnome Display Manager.
If you install the display manager, then Xorg will stop starting. If Xort doesn't start, then there is no low graphics error

---

### Post by sentinelace on 2013-01-05
> **sandyd said:**
> GDM stands for Gnome Display Manager.
If you install the display manager, then Xorg will stop starting. If Xort doesn't start, then there is no low graphics error

LOL okay and how do you install that?  I think I had lightdm installed before

---

### Post by sandyd on 2013-01-05
If you have lightdm, then remove lightdm

---

### Post by sentinelace on 2013-01-05
you used to be able to change the init script.  Has this changed?

---

### Post by sentinelace on 2013-01-05
what are the commands to remove both?  I did apt-get remove lightdm and it says cannot be found.

I also did apt-get remove gnome* and it removed it but on reboot I still get "low graphics mode" and I have to choose it to boot the the console.  When I install server from scratch it boots to the terminal.  What has changed?

---

### Post by lykwydchykyn on 2013-01-06
AFAIK lightdm did not exist in 10.04.  You need to uninstall gdm, like I said:
```

sudo apt-get remove gdm

```

removing gnome does not remove gdm, because other desktop environments can use gdm.

---

