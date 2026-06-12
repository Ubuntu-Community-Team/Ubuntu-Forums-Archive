---
title: "Problems with Wine and SketchUp"
date: 2010-07-02
forum: Wine
---

### Post by LucaLuke65 on 2010-07-02
Hi everybody, I'm quite new in ubuntu. I tried to use SketchUp with WINE. When I start the program, just after the SketchUp Welcome,  the following message appears: SketchUp is not able to initialize OpenGL. Be sure to have installed the right drives for your graphic card. Error: ChoosePixelFormat failed.
SketchUp was already working well under Windows on the same laptop.
Anybody can help me? Thank-you.

---

### Post by minio on 2010-07-04
hi,
do you have proper drivers with 3d acceleration installed? It shoud work out of the box with intel graphics, but for Nvidia and ATI cards you have to install them through System -> hardware drivers. If you have proper drivers than putting HKEY_CURRENT_USER\Software\Google\SketchUp6\GLConfig\Display\HW_OK=1 
into the registry could help. Of course the path could differ with SketchUp versions. To get to the registry type into the terminal - regedit - and press enter.

---

