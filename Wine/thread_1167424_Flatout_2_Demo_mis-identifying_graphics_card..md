---
title: "Flatout 2 Demo mis-identifying graphics card."
date: 2009-05-22
forum: Wine
---

### Post by random_hypocrisy on 2009-05-22
It identifies my Geforce 5800Ultra, as a 5600! It wont allow me to apply Anti Aliasing either, which Im guessing is related...

Is there a way to fix this?

---

### Post by cogadh on 2009-05-22
You may be able to set a registry entry in Wine that correctly identifies your card. See the [Useful Registry Keys]("http://wiki.winehq.org/UsefulRegistryKeys") page in the Wine wiki for details.

---

### Post by random_hypocrisy on 2009-05-23
> **cogadh said:**
> You may be able to set a registry entry in Wine that correctly identifies your card. See the [Useful Registry Keys]("http://wiki.winehq.org/UsefulRegistryKeys") page in the Wine wiki for details.

Thanks, but I have already done all that, and it still does it...

---

### Post by hikaricore on 2009-05-23
The nvidia-settings tool should handle antialiasing system-wide if I'm not mistaken.
Atleast this was the way it had to be done for games like WoW (to the best of my memory).

---

### Post by random_hypocrisy on 2009-05-23
> **hikaricore said:**
> The nvidia-settings tool should handle antialiasing system-wide if I'm not mistaken.
Atleast this was the way it had to be done for games like WoW (to the best of my memory).

I tried that, it just causes the demo to cancel out.

---

### Post by cogadh on 2009-05-25
Are you running Compiz/desktop effects (desktop effects are turned on by default when the proprietary driver for your video card is installed)? If so, that is likely the problem. When using desktop effects, it basically breaks OpenGL as far as Wine is concerned and can cause all sorts of weird problems. Try turning off desktop effects completely and see if it changes anything.

---

