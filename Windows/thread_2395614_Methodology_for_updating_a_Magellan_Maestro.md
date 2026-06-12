---
title: "Methodology for updating a Magellan Maestro?"
date: 2018-07-04
forum: Windows
---

### Post by bcschmerker on 2018-07-04
**I recently received a Magellan® Maestro™ 4370** (P/N 800-0061-001; S/N 0760223417633; software as of 4 July 2018 © 2008 Magellan Navigation Inc.; charts as of 4 July 2018 © 2013 Navteq) as a premium with a 1997 GMC® Safari™ intermediate-size passenger wagon.  Magellan Navigation apparently developed the onboard apps under Microsoft® Windows® CE™ while Win 5.2 (popularly known as Windows 2000 Professional Service Pack 2, Windows XP Home Service Pack 1, Windows XP Professional Service Pack 1, Windows XP Media Center Edition, and Windows Home Server) was still on the market.  Attempting to register and update the device on the ASUS® CM1630-06 as upgraded under WIndows 10.0.17134.137, I found to my chagrin that the available MiTAC International Corporation apps, viz., the current MiTAC SmartGPS™ Eco™ and the legacy Magellan® Content Manager™, do *not* recognize the '4370, though Windows itself did as "Magellan GPS" and assigned it four subdevices including a Volume "TFAT".

I have identified the Filename Extensions on this device's EEPROM and some of them date back to WordPerfect® 5.2 (as one of my contacts at facebook® had discovered).  Investigating available programs for what is showing itself an arduous task even in the preplanning, I found that Wine HQ&#8480; does not support CE hardware sufficiently to build new System Files, Applications, Dynamic-Load Libraries, and datafiles in the LinUX domain and cross-compile onto the '4370's planned upgrade Volume.  So, what tools *are* proven and available for building the update software?

---

