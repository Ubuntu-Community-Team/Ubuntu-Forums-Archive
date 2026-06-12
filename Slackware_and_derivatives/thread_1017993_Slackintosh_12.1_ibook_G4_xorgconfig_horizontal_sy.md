---
title: "Slackintosh 12.1 ibook G4 xorgconfig horizontal sync &amp; vertical refresh rate"
date: 2008-12-21
forum: Slackware and derivatives
---

### Post by boydrice on 2008-12-21
Hello,

Trying to install Slackintosh on my ibook G4. I am attempting to configure X using xorgconfig. However I am unsure what my horizontal sync or vertical refresh rate is. I have been scouring the internet and apple support to find this out. This is the details of my video card:
ATI Mobility Radeon 9200:

Chipset Model: ATY,RV280M9+
Type: Display
Bus: AGP
VRAM (Total): 32 MB
Vendor: ATI (0x1002)
Device ID: 0x5c63
Revision ID: 0x0001
ROM Revision: 113-xxxxx-142
Displays:
Color LCD:
Display Type: LCD
Resolution: 1024 x 768
Depth: 32-bit Color
Built-In: Yes
Core Image: Not Supported
Main Display: Yes
Mirror: Off
Online: Yes
Quartz Extreme: Supported
Display:
Status: No display connected

Does anyone know what settings I should use? Thanks in advance.

-Boyd

---

### Post by boydrice on 2008-12-21
Ok I guess I was making this way too hard on myself.  I just needed to run xorgsetup, now I have a KDE desktop.  Problem solved.

---

