---
title: "Cm2010 error?"
date: 2010-05-06
forum: Wine
---

### Post by KaiJordanDay on 2010-05-06
when I run:

> kai@kai-ubuntu:~/.wine/drive_c/Program Files/Eidos/Championship Manager 2010/CM2010_0$ wine ./CM2010.exe "/home/kai/Eidos/Championship Manager 2010/Save Games/b.CM2010-SaveGame"

I get this error (at the end) and the game closes down when it reaches 100%.

> drmRadeonCmdBuffer: -12. Kernel failed to parse or rejected command stream. See dmesg for more info.


Ubuntu 10.04

Wine 1.1.36

---

### Post by asdfoo on 2010-05-08
problem with your video drivers.

also I'm not sure the game will like "/home/kai/Eidos/Championship Manager 2010/Save Games/b.CM2010-SaveGame" 

It might need the windows path or just a relative path.

---

