---
title: "Steam games won't launch"
date: 2009-02-04
forum: Wine
---

### Post by JMuffin on 2009-02-04
I installed The Orange Box a while ago to play Portal, and everything worked fine. I should say that Portal worked fine. If I tried to play any of the Half Life's the games would load very slowly and I was never actually able to play them. I stopped playing Portal for a while and when I went back to it recently, I was unable to get any of the games to even launch.

I uninstalled and reinstalled The Orange Box, started up steam, and launched Portal. Everything looked fine but I had no sound. I exited the game to look for a fix for the sound issue but didn't really find anything and decided to try the game again without sound for the time being. Now when I try to launch any games in Steam I see a window that says "Preparing to launch <Game>" for a few seconds, then it closes and nothing happens.

Portal launched 5 minutes before this and I didn't change any settings. Has anyone else had this problem and found a solution?

Something odd I just noticed when I was looking for the version of wine I'm using to put here. According to synaptic I am currently using 1.1.9, but when I look in the about tab in winecfg it says I'm using 0.9.6. Any ideas there? thanks!

---

### Post by betrunkenaffe on 2009-02-05
I'd first off uninstall wine completely and make sure you get the newest one of 1.1.14, once you've done that and it shows that in the about tab then you should be fine on that oddness.

I had the same sound issue, set the launch option in steam to "-dxlevel 70" OR "-dxlevel 81" (81 worked for me, 70 crashed the games after a bit, but others have had 70 work instead of 81).

---

