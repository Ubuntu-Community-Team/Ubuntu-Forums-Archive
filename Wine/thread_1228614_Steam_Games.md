---
title: "Steam Games"
date: 2009-08-01
forum: Wine
---

### Post by TheLastGuardian on 2009-08-01
I was wondering.  What steam games run the smoothest on Wine (I also have PlayOnLinux installed).  Ones that i really would like to play on Linux (Im using Kubuntu) are both STALKER games, all Valve GoldSource and Source games, Civ 4 games, all Dooms, Enemy Territory Quake Wars, F.E.A.R 2, GTA3, and Sin1+Sin Episode Emergence.  I have a large game list on steam (about 180 or so) and i want to use linux more, not just for gaming, but it would be something i would like to do, and not always have to go back to windows to do

---

### Post by alexandari on 2009-08-01
well dude I dont know about all of them but CS Source ran smoothly on my computer using wine. Cedega has a support for Steam games but...dunno :<

---

### Post by TheLastGuardian on 2009-08-01
> **alexandari said:**
> well dude I dont know about all of them but CS Source ran smoothly on my computer using wine. Cedega has a support for Steam games but...dunno :<

Is Cedega the best thing to use for gaming on linux.  I know you have to pay either every 6 months or every year.  Does Cedega run others things than just games?

---

### Post by alexandari on 2009-08-01
It`s mainly for games. But it can emulate .exe files without problem. It has support...but I dont know. There are games that run better on wine than on cedega.

---

### Post by TheLastGuardian on 2009-08-01
> **alexandari said:**
> It`s mainly for games. But it can emulate .exe files without problem. It has support...but I dont know. There are games that run better on wine than on cedega.

ok. Are there any other programs for Linux that can work for games?

---

### Post by alexandari on 2009-08-01
Crossover. It`s a Wine project (I think) but it`s not open source. There`s a free 30 day version to download (was it 30 days? damn I cant remember...)
[http://www.codeweavers.com/](http://www.codeweavers.com/)

---

### Post by aoanla on 2009-08-04
> **TheLastGuardian said:**
> I was wondering.  What steam games run the smoothest on Wine (I also have PlayOnLinux installed).  Ones that i really would like to play on Linux (Im using Kubuntu) are both STALKER games, all Valve GoldSource and Source games, Civ 4 games, all Dooms, Enemy Territory Quake Wars, F.E.A.R 2, GTA3, and Sin1+Sin Episode Emergence.  I have a large game list on steam (about 180 or so) and i want to use linux more, not just for gaming, but it would be something i would like to do, and not always have to go back to windows to do

So. If by "all Dooms" you mean Doom and Doom 2 as well as Doom 3, then I should note that Doom and Doom 2 are DOS games, rather than Windows games (and the game engine has multiple linux ports).
So for Doom, Doom2, you'd be better off installing a native linux doom port (look in your package list to find some) and pointing it at the WAD files in your Steam install.
Doom 3 worked perfectly for me in Wine, but also has a linux port (again, install it and copy the relevant data from Steam if you want to use that).
Enemy Terrority: Quake Wars... has a linux port which worked brilliantly for me (again, copy stuff from Steam), but should work fine in Wine.
GoldSource games should be nigh perfect (just add -opengl to the launch options in Steam to make them use the most compatible graphics interface).
Source games, depends on the release of the Source engine. HL2-era Source engine is fine, TF2-era is mostly okay (but add -dxlevel 81 to the launch options to turn off DX9 mode), L4D-era appears to have more problems.

---

### Post by castlefox on 2009-08-05
What video card are you using?

---

