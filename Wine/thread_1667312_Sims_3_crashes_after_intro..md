---
title: "Sims 3 crashes after intro."
date: 2011-01-14
forum: Wine
---

### Post by Smari on 2011-01-14
Hello everyone.

I have been trying to install Sims 3 on my Ubuntu 10.04. Installation and running the game worked until the loading screen after the intro-video. Most often it crashes just before it is finished loading. Except for one time when it managed to finish bun then it crashed right after.

When it crashes the screen turns black and the sound lags for a few seconds but then stays quiet. Then I need to totally shut off my computer, because if I only restart it the screen stays black.

I have a nVidia Geforce 6600 GT. When it didn't work with the driver recommended by the "Hardware drivers" application in Ubuntu I updated the driver to the newest driver available for Linux on the nVidia pages. Nothing changed.

According to the System requirements you only need 128mb video memory in windows. But when I installed the game through PlayOnLinux it asks me how much memory my video card has and when I choose 128 it warns me that I will not be able to play the game without problems.

Are there different system requirements for programs run on windows then on wine? If so, then where can you find information about the system requirements in wine before you actually buy the program/game?

Other information:

Wine version: 1.2
Ubuntu version: 10.04

I can not get any terminal output because the computer freezes every time.

I have tried many different things with winetricks first I needed to install vcrun2005sp1 and d3dx9 to make it work (that was before I updated my PlayOnLinux to version 3.8.8 and reinstalled the game). 
Then I added some keys to the registry of wine in a new folder that i called Direct 3D

Videocard: nVidia 6600 GT 128mb.
Driver version : 260.19.29

Using PlayOnLinux version 3.8.8 and winetricks.

---

### Post by cogadh on 2011-01-14
If you are getting system freezes when running Wine apps, then there is very likely something wrong with your system completely unrelated to Wine. My first suspect would be the video card/drivers, especially considering you've already tried a couple different drivers. I suggest you do a complete uninstall/reinstall of the drivers, but just for the sake of troubleshooting, only use the restricted drivers Ubuntu normally offers.

I also would skip using PlayOnLinux for this. POL is great for games that require a lot of hoops to jump through in Wine, but for a game like The Sims 3, which for the most part "just works" in Wine, it adds an extra unnecessary layer to the process.

Lastly, the system requirements in Wine are really no different than they are in Windows. Some people do like to pad them a little because you are adding an extra layer (Wine) to the normal process of running the game. Personally, I don't do that because Linux is already using fewer resources than Windows does on its own, so that gain balances out any loss from Wine and you pretty much break even.

---

