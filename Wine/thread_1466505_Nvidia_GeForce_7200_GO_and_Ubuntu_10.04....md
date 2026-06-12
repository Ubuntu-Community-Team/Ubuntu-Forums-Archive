---
title: "Nvidia GeForce 7200 GO and Ubuntu 10.04..."
date: 2010-04-30
forum: Wine
---

### Post by ickyplush on 2010-04-30
1.6GHz Centrino Duo
2GB
Nvidia GeForce 7200 GO

In Windows I was able to play some fairly basic games, 
CS:S 
Sims 3 (medium settings) 
lol even gave Crysis a go a low settings (litteraly 5-10 FPS),

 just wondering what kinda games I could be expecting to run under WINE, 
assuming there will be a certain degree of loss in preformance under WINE

Ick

---

### Post by cogadh on 2010-04-30
As long as you have the restricted drivers for that video card installed, you should be able to play any games that you A) already meet the minimum requirements for and B) already work in Wine. You can check [Wine's Application Database]("http://appdb.winehq.org/") to see what games will and won't work in Wine

---

### Post by ickyplush on 2010-04-30
Thanks for the help, I was basically just asking
would I be expecting any significant decrease in performance?

Ick

---

### Post by cogadh on 2010-04-30
Possibly. It really depends on the game. [CS:S]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731") and [the Sims]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664") should be comparable in performance, while I personally wouldn't even bother with [Crysis]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=5880").

---

### Post by jkxx on 2010-05-01
If the game you are running has an OpenGL mode it will run just as fast in wine as it does in Windows, unfortunately few games support OGL.

If it's an older DirectX 7-8 game, it might actually work faster in wine due to some recent optimizations.

For DirectX 9 games (the vast majority), wine will be a bit slower, depending on the game. As cogadh said, don't even bother with crysis with that video card. From what I've read of that game you would need a more powerful card to run it, even under windows.

---

