---
title: "Need some advice of how make WoW work on Ubuntu Hardy"
date: 2008-12-29
forum: Wine
---

### Post by Jeffbot on 2008-12-29
Hey everyone. Ive just picked back up on ubuntu and I am trying to get WoW to run, which it does, kinda.  When I installed the game I used the d/l from wow.com and used wine to install it, then it updated and so forth. I followed the help forums found on this site and i cant play, ive made the corrections in the config.wtf file to no success. Ive also installed Directx 9.0c with failure being the result.  the EULA screen is so scrambled i cant see the background. when i add the line for OpenGL the game wont even start. ive been fighting this for 3 days now, does anyone have any ideas?


intel T2400
ATI x1400
2g ram

---

### Post by OrbJinzo on 2008-12-30
first off youll need to totally uninstall wine... and that includes removing the ./wine file and reinstalling it. then reinstalling WoW I know its a daunting task but this will give you a fresh install. 

First off do you have your drivers for your video card installed? If not i would go there first. 

Secondly I would try making a config.wtf file for WoW then running it. Also to force wine to run in opengl i would add the registry key for DirectDrawRenderer = OpenGL. Theres is a guide on this forum for doing that.

---

### Post by hikaricore on 2008-12-30
Just FYI you should never installed DirectX under WINE unless you know what you're doing.
It can/will screw things up and is not needed in almost all cases.

---

