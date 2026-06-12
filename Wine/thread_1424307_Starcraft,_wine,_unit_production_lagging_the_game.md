---
title: "Starcraft, wine, unit production lagging the game"
date: 2010-03-07
forum: Wine
---

### Post by Shadyboy on 2010-03-07
Hello.
Ubuntu 9.10 32 bit system.

My lspci if info is needed :
[http://pastebin.com/8s5R3AZ1](http://pastebin.com/8s5R3AZ1)

My Xorg.conf file, if my problem is in there by any chance:
[http://pastebin.com/pNMUU5k1](http://pastebin.com/pNMUU5k1)

Wine, Starcraft with Brood War ( digital copy from Blizzard ) and the open source ATI driver.
Can it run Starcraft game 100 % smooth?
I have installed the newest wine ( wich is 1.1.40 atm ) and Starcraft ( wich I have updated to the newest, dont remmember what version number it is)
I can start the game, movies work, battle.net ever works for me after I manually updated the game.
But the game laggs when I have a group of units ( more then 7 or 8, its different for each of the 3 races ) and whene I produce more units either at 
"barrack" buildings or "headquarter" buildings ( Command senter, hatchery, or the Nexus )
It laggs so much that it is un-playable when I do. 

I am now wondering on if there is anyone out here, who knows of a sollution for my "lagging".
Or any "tweaks" i can do to stop that lagg...

---

### Post by asdfoo on 2010-03-09
> **Shadyboy said:**
> Hello.
Ubuntu 9.10 32 bit system.

My lspci if info is needed :
[http://pastebin.com/8s5R3AZ1](http://pastebin.com/8s5R3AZ1)

My Xorg.conf file, if my problem is in there by any chance:
[http://pastebin.com/pNMUU5k1](http://pastebin.com/pNMUU5k1)

Wine, Starcraft with Brood War ( digital copy from Blizzard ) and the open source ATI driver.
Can it run Starcraft game 100 % smooth?
I have installed the newest wine ( wich is 1.1.40 atm ) and Starcraft ( wich I have updated to the newest, dont remmember what version number it is)
I can start the game, movies work, battle.net ever works for me after I manually updated the game.
But the game laggs when I have a group of units ( more then 7 or 8, its different for each of the 3 races ) and whene I produce more units either at 
"barrack" buildings or "headquarter" buildings ( Command senter, hatchery, or the Nexus )
It laggs so much that it is un-playable when I do. 

I am now wondering on if there is anyone out here, who knows of a sollution for my "lagging".
Or any "tweaks" i can do to stop that lagg...

Some important things:

Wine version: newer is usually better, ie the development or beta version.  1.1.40 is the most recent.

Video driver:  I see you have ati, if you are not supported in the most recent fglrx, you should look at using the free software drivers, the most recent versions usually have improvements over the ones shipped with ubuntu, but upgrading this is more suitable in another section of the forum.

Setting ddraw render to opengl:

wget kegel.com/wine/winetricks && sh winetricks ddr=opengl

---

