---
title: "Ubuntu Server doesn't boot without Monitor"
date: 2009-07-23
forum: Server Platforms
---

### Post by swissuriel on 2009-07-23
This is driving me insane: i cnnot boot my 9.04 Server without a Display. 
the 2 or 3 suggestions I found via google led me to x.org configurations. Unfortunately this doesn't help me, because I never installed GDM etc etc (I installed the system using the Server image and did not install any X related stuff other than what gets installed by default)

If someone could point me to the right direction, it would be really nice.
Ubuntu Server runs on a ALIX1d Board (details can be found via []("http://www.pcengines.ch"))
Basically it's a AMD Genode Platform.

Sorry for the whining.

---

### Post by cdenley on 2009-07-23
Will any software boot on your server without a monitor? It is probably hardware-related. Perhaps there is a BIOS setting. Do you have a video card installed? You can try removing or replacing it.

---

### Post by swissuriel on 2009-07-23
If by "any Software" you mean other OS'es then yes; OpenBSD worked. 
The Server hangs while booting. if I connect a Monitor after i turned the Server on, the only thing I see is the line "boot from blabla (hd0 blabla". nothing else.
The system doesn't have a graphic card. i can try to disable the onboard craphic chip in the BIOS.
(although I do not remember the BIOS offering this option)

---

### Post by swissuriel on 2009-07-23
Unbelievable
It was a BIOS Option that was set by default
Sorry for the noise, now I feel relieved and happy because of Your help and f$$*** annoyed by my stupidity at the same time.

Thank You.
Thank you very much!

---

