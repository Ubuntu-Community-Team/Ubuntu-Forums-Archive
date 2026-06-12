---
title: "Cedega and Day of Defeat: Source"
date: 2009-09-22
forum: Wine
---

### Post by boards-of-canada on 2009-09-22
I'm rebuilding a machine from scratch but want to make sure I can at least play my one game in Cedega. 

Has anyone tried Day of Defeat: Source in Cedega? If so, what is the performance like? Also, what type of graphics card you using?

(Sorry, I haven't built a computer in over five (5) years and I just want to make sure the new one I build will be able to do it in Ubuntu. I'm tired of booting in XP just to play one game.)

---

### Post by dagoth_pie on 2009-09-22
I gave it a quick Google, and one interesting thing I came across was that it's built on GoldSrc which is a modified quake engine, so theres too possibilities, it might be possible to take ioQuake and modify it to make it run the game data, or more probably, it may be possible to hack the game and make it run OpenGL instead of DirectX (if it doesn't already use OpenGL by default), so I'd guess that it's quite likely that it will be possible to run it under wine. As for how powerful of a computer you'll need I can't really say, maybe someone else can.
Good luck

EDIT: Actually thinking about it, I think Source was the HalfLife engine which was rewritten to run DirectX for a while, Hopefully I'm wrong though.

REEDIT: From Wikipedia > GoldSrc is able to render in two APIs &#8722; OpenGL and Direct3D.

---

### Post by ELD on 2009-09-22
It is not made on a quake engine.

Day of Defeat "source" is built using the "source engine" like counter strike "source" and half life 2.

Source engines run well ine WINE no need for Cedega, if you want to pay for support and so forth use Crossover Games, far better than Cedega.

It will not need a powerful computer, source engine games are rather dated now.

---

### Post by beastrace91 on 2009-09-22
> **ELD said:**
> Day of Defeat "source" is built using the "source engine" like counter strike "source" and half life 2.

Source engines run well ine WINE no need for Cedega, if you want to pay for support and so forth use Crossover Games, far better than Cedega.

It will not need a powerful computer, source engine games are rather dated now.

It is indeed Source Engine. It will run VIA Wine. Some games Cedega does run better (Crysis, Left 4 Dead, and a few others) but if you want to play DOD:S just use Wine - or as suggested use Codeweavers, I currently have both a Codeweavers and Cedega subscription and I much prefer the former (will not be renewing my Cedega when it expires at the end of the year)

As for the last bit even though Wine technology has come a LONG way in recent years there is still a sizeable performance decrease running most games through it. On my nVidia 260m with a pile of optimizations (including running in Direct X 8.1 mode) I still maybe get a steady 40fps in TF2 (runs on the same OB engine as DOD:S) in combat. I have DOD:S let me give it a load up on Codeweavers and see what the default performance is like.

EDIT: On my system with settings at defaults running at 1280x960 resolution I average around 30fps, setting dxlevel to 81 increases it to around 50.

~Jeff

---

### Post by boards-of-canada on 2009-09-22
Thank you for the responses. 

Seems like NVIDA is better for linux.

Think this will work:

EVGA 512-P3-N871-AR GeForce 9800 GTX+ 512MB 256-bit GDDR3 PCI Express 2.0 x16 HDCP

???

---

### Post by ELD on 2009-09-22
Graphics card looks fine :)

---

### Post by beastrace91 on 2009-09-22
> **boards-of-canada said:**
> 
EVGA 512-P3-N871-AR GeForce 9800 GTX+ 512MB 256-bit GDDR3 PCI Express 2.0 x16 HDCP

That will work swimmingly! (My 260m performs at around the same speed as a 9800 desktop card) My advice is to be sure to use the 190.xx beta drivers as I saw a good FPS increase when upgrading to them from the 18x.xx drivers.

~Jeff

---

### Post by boards-of-canada on 2009-09-23
Thank you guys. I really appreciate it.

---

