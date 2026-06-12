---
title: "My nVidia driver doesn't show up in Hardware Drivers"
date: 2008-07-28
forum: Virtualisation
---

### Post by Virtua-Touch on 2008-07-28
My nVidia driver for my 6600 GeForce card won't show up in the Hardware Drivers in my Ubuntu guest. What must I do to make this work?

---

### Post by Shazaam on 2008-07-28
At this time virtualization apps use their own "video card or driver" hard coded into their respective programs. So you cannot install drivers for your physical video card on your guest os. The best thing you can do is install their tools/guest-additions on the guest os to improve graphics.
On a Windows guest you can change the video driver from "VGA" to "SVGA" in Device Manager also.

---

### Post by Virtua-Touch on 2008-07-29
Alright. I need to find my Dad's WinXP CD or Win98 so I can install a WinXP/98 guest inside my WinXP host lol.

---

