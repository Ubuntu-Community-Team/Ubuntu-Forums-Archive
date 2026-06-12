---
title: "GAZV3 Mouse heads to screen corner"
date: 2008-11-21
forum: System76 Support
---

### Post by AusIV4 on 2008-11-21
In the past two days there have been several times that the cursor has stopped doing what I was telling it and taken off towards one corner of the screen. I'm not sure if this is a hardware problem, or if its related to my recent update to intrepid.

[EDIT]
I should note, as soon as the mouse gets to the corner, it stops the phantom movement and I can take it back where I want it.

[EDIT AGAIN]
Disabling compiz seems to have fixed this, so I'm guessing it's a problem (or feature?) with some plugin I didn't previously have enabled. I'm not marking this solved until I've gone a couple hours without phantom movements, but it inspires confidence. After that, I'll try and figure out what plugin is causing the problem, and file a bug report with that (if it's not intended as a feature).

---

### Post by thomasaaron on 2008-11-21
I've not seen that before. I'd be surprised if it is intrepid (especially since nobody else has reported this issue).

1. Are you sure you're not accidentally brushing the touchpad?
2. Do you have an external mouse hooked up at the same time?

---

### Post by AusIV4 on 2008-11-21
The first few times I wasn't sure whether or not I had brushed the touchpad, but by the time I posted this I was absolutely certain. The first time I observed it, I was using Synergy to use the keyboard and mouse from another computer, but I have since observed it without synergy. It almost always happens on key presses or mouse clicks, but I haven't figured out how to reliably reproduce it.

It seems to have stopped after disabling Enhanced Desktop Zoom in compiz (which I believe I enabled manually, thinking I'd used it in Hardy), but before it stopped I was able eliminate all non-software possibilities. On a couple of occasions, the mouse moved to the exact center of the screen. Since the touchpad detects relative movement, it has no concept of the center of the screen.

---

### Post by tom480 on 2008-11-21
I'm having the same problem as described by AusIV4, cursor spontaneously parks itself in one of the screen corners, but allows me to return it to wherever I'm working.  Have seen it in Firefox and Open Office Word Processor.  Very annoying, but not fatal.

Details:
Linux rookie, not ready to commit existing data to Linux
Ubuntu 8.10, AMD64 edition
Homebuilt desktop (no touchpad, no Compiz)
Logitech optical usb mouse
AMD 4800 processor, 2g ram, Nvidia 9200 graphics card

All suggestions gratefully accepted.

---

### Post by thomasaaron on 2008-11-21
Have you tried AUSIV4's suggestion yet?

EDIT: How do you have no compiz? 8.10 comes with it installed an enabled. Do you mean that you have desktop effects turned off?

---

### Post by tom480 on 2008-11-21
Many thanks for your questions, TA.  As you can easily see, there is no false modesty in my claim to rookie status.  

Your comment, "How do you have no compiz? 8.10 comes with it installed an enabled. Do you mean that you have desktop effects turned off? " sent me on a search of my setup.  I right-clicked the desktop, went to Change Desktop Background.  The window Appearance Preferences tab labeled Visual Effects offers three choices.  I have had None checked since my initial boot-up.  Does the None option turn off the Compiz that is the subject of this discussion?  If not, could you point me in the right direction?

Thanks for kicking me a notch further up the learning curve.

---

### Post by AusIV4 on 2008-11-22
I've re-enabled Enhanced Zoom, and the problem is still gone. It may be one of the conflicts that was resolved when I enabled standard zoom.

Now I'm just kind of confused, but I'm glad its working.

---

