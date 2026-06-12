---
title: "Using Battlefront 2 in Wine"
date: 2011-01-17
forum: Wine
---

### Post by hansolo4949 on 2011-01-17
I have a laptop with Ubuntu 10.10 on it, fully patched, with the latest stable version of Wine on it. I tried to install BF2 on Ubuntu using playonlinux, and that's when the problems started...

I couldn't install it from playonlinux, because it wanted a cd, and I had it on a dvd. I then tried to use Wine, and it installed, but the normal run won't work, because for some reason Wine won't see the BF2 dvd. It would run from the "safe" mode, but I couldn't see half of the things on the screen (it was whited out...completely), and when I managed to load a mpa, it stuck on the loading screen. I finally decided to uninstall it, although I have no idea why it won't work, because it gets a "bronze" rating in Wine HQ, and the reviews said it worked. I think I might need Wine v.3, but how do I install it?

Thank for your help!

---

### Post by runrun395 on 2011-01-22
Yeah I've also been trying to get Battlefront II to work. I tried it in VirtualBox, but it was useless; VirtualBox hasn't developed the graphics enough for gaming. I just finished installing XP on a separate partition, maybe it's the only way.

mostimpressive

---

### Post by hansolo4949 on 2011-02-28
Yeah, but I would really like to be able to run the applications I run in Windows on ubuntu. Quite honestly, thats the only thing that is keeping me from removing Windows and sticking with ubuntu.

---

### Post by eerror on 2011-04-14
I have Battlefront 2 (legit dvd) so I decided to give a shot ... again.  I had no luck with it a few years ago (same hardware except for ram and hd) but it appears Wine has been improved enough to make it run very well.

Here are the specs for my laptop.  This is almost a 4 year old laptop (except for the ram and hd upgrade).
HP DV6000, AMD Turion 64bit X2 Mobile TL52 1.6Ghz, 4GB RAM, 120GB SSD.
nVidia Geforce Go 6150.
DVD writer is Slimtek DVD A  DS8AZH

Ubuntu 10.10 (64bit) patched up (as of 2011.04.13)
wine-1.2.2

I ran the SWBF2 installer via wine.  Installed fine and fast, no issues there.  I opted out of installing xfire and other things it asked me about.

MINOR ISSUES RUNNING THE GAME:
1) The game itself has to be run in Safe Mode.  The regular mode doesn't seem to work for me.
2) Loading of level takes forever.  5 minutes on the load screen and you will think it froze but it didn't (no hd activity).  Once it loads it's fast.  I had _no_ issues with graphics.  Shooting, jumping, sound etc, it's all working and it's fast.  Basically I couldn't tell it wasn't Windows.

So there you have it.  Miracles do happen :)
Star Wars Battlefront 2 does work on older hardware with Ubuntu 10.10 and Wine.

Good luck with your install.  That game is an oldie but a goodie :)

---

### Post by MaindotC on 2011-04-24
I got it working but there are a few glitches.  I installed the directx9 package using winetricks which really made the difference.  I can't seem to connect to multiplayer games (which kills it) but I could play single player successfully.  The only real problem is that it took roughly 5 - 7 mins to load before starting a mission.  The loading bar at the bottom - it would load up just fine, but the actual mission wouldn't start for 5 - 7 mins after that.  Audio is good, video is good, just hate waiting for 5 - 7 mins between missions :)

---

