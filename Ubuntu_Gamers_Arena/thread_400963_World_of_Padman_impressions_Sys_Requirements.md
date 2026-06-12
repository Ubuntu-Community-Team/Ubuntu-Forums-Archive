---
title: "World of Padman: impressions? Sys Requirements?"
date: 2007-04-04
forum: Ubuntu Gamers Arena
---

### Post by 3rdalbum on 2007-04-04
A few days ago I saw World Of Padman on UGA. The Youtube trailer made my mouth salivate - this game looks seriously cool!

Has anyone played the demo yet? Is it as fun as it looks?

Also, the screenshots make it look very GPU-intensive. I've got an ATI Radeon Xpress 200 and 1.2 gigs of RAM, and Nexuiz runs very sluggishly. How does WoP run in comparison to Nexuiz on lowest detail settings?

---

### Post by Perfect Storm on 2007-04-04
My specs are;

P4 2.4 Ghz 1024 (800mhz) ram
GF 6600 GT 256 mb

runs without a glitch even high res (1600x1200).

[quote=from argie]
It runs on my Intel Pentium IV 2.9 Ghz with 256 MB RAM and onboard VIA graphics with 32 MB shared. This doesn't play Nexuiz at all, but WoP works just fine at 640x480.
[/quote]

So if you fiddle a little with the options, I'm sure you can get it running.


Better if you had a nvidia card for sure, but try anyway. It's really good.

---

### Post by compiledkernel on 2007-04-04
Assuming that its q3base, and it most indeed is. I would have to assume that q3 reqs are in order for minimums. 
Not that i would recommend this, but its probably as "low as you go". 
----

3D graphics accelerator with full OpenGL support, 
Pentium II 233 MHz or AMD 350 MHz K6-2 processor or Athlon processor, 
64 MB RAM, 
8 MB video card, 
500 MB of free hard drive space, 
100% DirectX 3.0 or higher compatible sound card, 
CD-ROM drive (600 kB/s sustained transfer rate)

---

### Post by cprofitt on 2007-04-05
The game play reminds me of the first SiN game.

---

### Post by bonzodog on 2007-04-07
The game is awesome, and runs really well on my system. I am loving playing this!

---

### Post by crane on 2007-04-08
Yep, cool game here. Runs great on my system. My daughter and I have been playing padmaps on Q3 for a while. his is really fun, A little dark but I should be able to tweak that up. What's really funny is the fact that it runs so great under Linux but I can't get it running under windows. I wonder if that OS will ever catch up to Linux is quality and dependability:lolflag:

---

### Post by Perfect Storm on 2007-04-08
Just set ignore gamma to off in Padman, then you should be fine.

---

### Post by Popoi on 2007-04-12
Is there an Online mode on WoP? Or is it completly Online? :o

---

### Post by compiledkernel on 2007-04-12
Do believe its online and single player as well. Someone correct me if not.

---

### Post by Perfect Storm on 2007-04-12
At the moment it's multiplayer/onlineplay, they are working on to make the final steps for implementing singleplayer as well.
People couldn't wait so they decided to release the multiplayer part first.

---

### Post by fakie_flip on 2007-04-21
WoP and other games are dark when I play them, so I do a command to brighten the screen before playing the game. I'm sharing it for anyone else who has the same problem.

xgamma -gamma 1.7

When you exit the game, your screen will probably be too bright. To restore it, just do this.

xgamma -gamma 1.0

---

### Post by hikaricore on 2007-04-21
WoP has it's own gamma option somewhere to fix it's problem.
I forget what menu it's under so search around.

---

### Post by Cresho on 2007-04-28
> **crane said:**
> Yep, cool game here. Runs great on my system. My daughter and I have been playing padmaps on Q3 for a while. his is really fun, A little dark but I should be able to tweak that up. What's really funny is the fact that it runs so great under Linux but I can't get it running under windows. I wonder if that OS will ever catch up to Linux is quality and dependability:lolflag:

there is a setting in the game where you can disable the settings->display and disable "ignore HW"  the game will start with intense and awsome colors.!!!!! brightness is up as well without killing the dark and dark looks like real dark.

---

### Post by fakie_flip on 2007-04-30
I've been having a problem with brightness in Feisty. Maybe this is a bug I have because I upgraded from Edgy to Feisty, and I should install fresh from a Feisty cd. I increase my brightness, but after about 5 minutes or so, the brightness goes back to what it was, dark again. This happens when I use the xgamma command or the brightness controls from a game. The only solution I have found to this problem is to make a for loop in bash that keeps running the xgamma command over and over, so as soon as it goes dark, it comes back to bright again. I put a pause in the loop using the sleep command.

---

