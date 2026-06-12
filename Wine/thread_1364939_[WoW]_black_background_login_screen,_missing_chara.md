---
title: "[WoW] black background login screen, missing character models"
date: 2009-12-26
forum: Wine
---

### Post by AilesGrises on 2009-12-26
And an extremely low framerate. My computer can handle WoW at about 30-40 FPS in Windows, but in  Wine it goes at about 5-10 FPS.

According to
[https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft")
all I have to do is put
SET M2UseShaders "0"
in the WTF file and it will fix this, but it doesn't seem to have worked.

Edit: After much testing, the regedit fix it suggests doesn't seem to do anything.
Putting SET M2UseShaders "0" in the wtf file doesn't seem to affect anything
Using OpenGL instead of Direct3D gives me models and login screen background, but black boxes and weird things in the background in-game. Direct3D seems to do the exact opposite.
The only thing that seems to have any positive effect is SET ffxDeath "0"
SET ffxGlow "0" which brings the framerate up to normal.

I'm running 1 gig of RAM, 1.6 GhZ Dual Core processor, and an integrated graphics card 8 MB.

---

