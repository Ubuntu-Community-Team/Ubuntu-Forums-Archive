---
title: "Ati, wine and TF2 (online source games)"
date: 2010-01-28
forum: Wine
---

### Post by Duskao on 2010-01-28
Hey guys. I'm not sure if many of you have been having the same issues I have been having for the last couple of months trying to run online source games with steam through wine using an ati vid card, but I have a bit of good news. I have made some serious progress. I think there was an issues with the Catalyst 9.12 (fglrx 8.682) drivers from Ati with the afore mentioned games. When I would try to run these games with these drivers on my machine (AMD X3 8650 2.3 Ghz, 2 Gigs DDR2 667 RAM, Radeon HD 4850) it would crash out of the game quite quickly. Generally within a few minutes (5 or 10 if I was lucky). However, since I have updated to the newest 10.01 catalyst driver, it's like night and day. Has this cured crashes??? No... However, it has certainly prolonged my TF2 experiences. I am crashing much less frequently and I am able to run the game with higher settings for much longer (round an hour). And this is with all the same tweaks. 

So basically to sum it up, if your running an Ati vid card and trying to play online source games through wine with a recent card (non legacy) I would recommend updating your video driver. 

Just so everyone knows, I have used many tweaks new and old to try to get this running properly. So far my best experiences have been just with a basic install of steam then downlaoding TF2 (or one of the others as you normally would with steam). Then in the settings for the game, in launch options I use -heapsize (whatever RAM you allocate for the game in kilobytes)-dxlevel 80 or 81(only use once to start game then close and remove from launch options) -novid -console (for in game tweaks)

For wine tweaks check out [http://appdb.winehq.org/objectManager.php?sClass=application&iId=5823](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5823)

You can also try an interesting little tweak program for TF2 with [http://www.dieall.de/da2008/index.php?mod=articles&action=view&id=60&page=3](http://www.dieall.de/da2008/index.php?mod=articles&action=view&id=60&page=3)
It can be very useful but the newest release (2.7) won't install for me but the 2.1 release works great.

Another great place for tweaks of source stuff is [http://www.tweakguides.com/HL2_7.html](http://www.tweakguides.com/HL2_7.html)

Best of luck to all.

---

### Post by settface on 2010-12-14
i'm running tf2 on wine1.3 with the Catalyst 10.12 ATI/drivers for my HD3870. after days of tweaking and trying to find a good compromise i have come across this bug report which proposes a workaround: [http://bugs.winehq.org/show_bug.cgi?id=24166]("http://bugs.winehq.org/show_bug.cgi?id=24166")

not entirely sure if it's the same bug that all ATI users are experiencing but so far i haven't had the usual lock-up(freeze) in the game. however, the tf2 client will time out and get kicked from the server quite frequently instead - probably due to the nature of the workaround.

ps: a tip to get good framerate with decent quality is to lower the model details but set the texture detail high.

---

