---
title: "Thoughts and screenshots of mobile-i386 image"
date: 2008-10-23
forum: The Cafe
---

### Post by MethodOne on 2008-10-23
When I boot the Intrepid mobile-i386 image, it looks nothing like the Netbook Remix interface.  It's just regular GNOME with larger (than the regular desktop images) panels at the top and left of the screen. Attached are some screenshots of it.  I wish we had some official USB images of the regular desktop images in both architectures.

---

### Post by the yawner on 2008-10-23
I believe that's for mobile devices (smartphones) which usually have smaller screens than netbooks.

---

### Post by MethodOne on 2008-10-23
> **the yawner said:**
> I believe that's for mobile devices (smartphones) which usually have smaller screens than netbooks.

The download page says:

"'This  USB image is optimized for ultra-mobile PCs and netbooks with screens up to 10""

I tested this image on my Eee PC 701 and it looks too big for the screen.  The Netbook Remix interface looks better.

---

### Post by NRios on 2008-10-29
I'm pretty sure the image is wrong, and we're getting the MID version. Quoting from releases.ubuntu.com

_Mobile USB Image:_ This USB image is optimized for ultra-mobile PCs and netbooks with screens up to 10"

_MID USB Image:_ This USB image is optimized for handheld devices with 4-7" [COLOR="Red"]*touchscreens*[/COLOR] and limited processing power

However, when you boot the Mobile USB Image, ubuntu-8.10-rc-mobile-i386.img, you get a virtual keyboard, a touchscreen calibration panel, a touch-controlled web browser, extremely large sized widgets and fonts for a 10" or 7" screen, an enormous sidebar that is locked in place, no Network Remix launcher.

This configuration is obviously for MID. I thought there might some sort of launch option to select the Netbook view, but now I'm sure that the file that has been posted is wrong. I'll try to report a bug.

---

