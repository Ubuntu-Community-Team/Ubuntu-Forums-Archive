---
title: "Login loop"
date: 2017-10-05
forum: Ubuntu Development Version
---

### Post by Sindile_XJ_Bidla on 2017-10-05
I have just upgraded my desktop to latest beta release from 17.04
At the login screen choosing either Ubuntu or Ubuntu on Xorg I am unable to login. I get returned to the login screen.
I have removed .Xauthority file and reinstalled gdm3 and ran dpkg-reconfigure

---

### Post by dino99 on 2017-10-05
If that installation is a dist-upgraded one, then run 'gtkorphan & bleachbit (as root) to clean the system. Then if the loop is still there, try using lightdm instead.
It also can be related to the graphic driver used.

---

### Post by jbicha on 2017-10-05
You might have hit [LP: #1717923]("https://launchpad.net/bugs/1717923")

See the workaround there.

---

### Post by Chanath on 2017-10-06
> **jbicha said:**
> You might have hit [LP: #1717923]("https://launchpad.net/bugs/1717923")

See the workaround there.

I have the loop in another way; "on Xorg" is on a loop, not Wayland. It boots only on Wayland.
I don't have [COLOR=#333333][FONT=monospace]~/.config/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]monitors.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]xml at all. My [/FONT][/COLOR][COLOR=#333333][FONT=monospace]~/.config/ is below.[/FONT][/COLOR]

---

### Post by jbicha on 2017-10-06
Chanath, what graphics driver are you using? My understanding is that Nvidia currently only works with X, but there is a hack to make it work with Wayland (but that will break X).

---

### Post by Chanath on 2017-10-06
> **jbicha said:**
> Chanath, what graphics driver are you using? My understanding is that Nvidia currently only works with X, but there is a hack to make it work with Wayland (but that will break X).
i915 in both laptops. In one it works both in Xorg and default works, in the other it has this loop.

Anyway, once the final is released, I'll install again, for both are test installs now.

---

