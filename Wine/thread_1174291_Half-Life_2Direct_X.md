---
title: "Half-Life 2/Direct X?"
date: 2009-05-30
forum: Wine
---

### Post by thisnamestoolong on 2009-05-30
Whenever I try to launch Half-Life 2 from Steam, I get an error telling me that I need to install the latest version of DirectX. I have an Asus G50V laptop with a GeForce 9700M video card. I have the drivers from NVidia installed properly, and my Wine install seems clean. I tried using the real dx9 DLL from a DirectX 9 install, but to no avail. Any thoughts on why HL2 is not seeing the DX in wine?

---

### Post by Duskao on 2009-05-30
There should be no need to install direct x. It is actually built into wine. If I were you, I would remove wine and delete your .wine folder, then reinstall it. And then install steam and half-life 2 through steam. Or install them off of disc. Also when you are going to play, you are likely going to want to use direct x 8 anyway, as you get better performance with it. To do this, you need to go into your games list, then click a game and click properties, then set launch options then "-dxlevel 80" no quotes. Or you can use dx 7 with 70 instead of 80 or 8.1 with 81.

---

