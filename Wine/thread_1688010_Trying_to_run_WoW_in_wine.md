---
title: "Trying to run WoW in wine"
date: 2011-02-14
forum: Wine
---

### Post by DAC1138 on 2011-02-14
I'm trying (but failing miserably) to run World of Warcraft in Wine. I can get the game to load, but the graphics are all messed up. I have a screen shot in case anyone is curious to see what it looks like. It's all jumpy and jittery.

I know I have an intel card and it's not ideal for gaming, but the game runs smoothly in Windows 7. From my past experience with wine/windows gaming, I've had better luck with games running smoother in linux than on windows. Running WoW in openGL is a lost cause, so I'm told, because I have an intel graphics card.

GLX gears shows I get 300 FPS, so I'm expecting semi playable speeds.

a link to the screenshot: [http://img25.imageshack.us/i/screenshotlf.png/](http://img25.imageshack.us/i/screenshotlf.png/)

---

### Post by Tweak42 on 2011-02-15
The graphical glitching you are getting is likely from running Wow in D3D (Direct3D) mode.  Wow runs fastest and least glitch in opengl mode but even then the performance is not on par with windows equivalent.  Try running in opengl mode anyway, but I would not get your hopes up as many on this board have tried intel opengl with gaming and that has been mostly fail. 

According to: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549)  the intel opengl driver should work, but lacks in performance.

GLXgears is not good indicator of performance for gaming, it best suited as a simple quick test to verify that opengl drivers are working.  FYI: I get @2500 fps in glxgears, and at lowest settings I can just move around in Stormwind at <10fps when it's semi busy.

---

### Post by DAC1138 on 2011-02-16
If I try OpenGL mode, it always loads and freezes at a white screen. I can't see anything or hear anything and it freezes immediately.

---

### Post by Tweak42 on 2011-02-16
> **DAC1138 said:**
> If I try OpenGL mode, it always loads and freezes at a white screen. I can't see anything or hear anything and it freezes immediately.

Hmm... well you are in a uphill battle.  If you have the patience to go at it, you might try experimenting with some of the less documented graphics settings in Wow's WTF file, wine registry tweaks and even different opengl driver versions.

---

### Post by DAC1138 on 2011-02-19
> **Tweak42 said:**
> Hmm... well you are in a uphill battle.  If you have the patience to go at it, you might try experimenting with some of the less documented graphics settings in Wow's WTF file, wine registry tweaks and even different opengl driver versions.

I definitely have the patience. Since I have the Windows partition, I'm in no rush. I'm mostly trying to get it to work under linux to prove to myself that I can do it and I want to see if I can get it to perform better than windows, once I do (if I do) get it running in OpenGL mode. It's curiosity that has me setting this goal.

---

### Post by gradinaruvasile on 2011-02-19
You probably wont have it running with intel cards. The drivers are crap compared to their Windows counterparts. They are not good at all to play any semi-demanding 3d games.

The glxgears score is very very low BTW. You should get at least 1000 with intel cards with a decent dual core cpu. But you wont get any decent 3d game to work with it because the lacking opengl implementation of the drivers.

Bottom line: buy a nvidia dedicated card. That is, if you have a desktop.

What hardware do you have anyway?

---

