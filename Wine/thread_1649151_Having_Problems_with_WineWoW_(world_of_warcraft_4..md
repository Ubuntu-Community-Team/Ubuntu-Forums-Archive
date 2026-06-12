---
title: "Having Problems with Wine/WoW (world of warcraft 4.0.x)"
date: 2010-12-19
forum: Wine
---

### Post by Lintnewbie on 2010-12-19
Having problems getting the graphics to work (login screen is a black background and white text). I don't know if WoW will run on my laptop due to specs or if its mint 10. I do have compiz working with the rotating cube so I know the right drivers are in.
laptop specs
[http://reviews.cnet.com/laptops/toshiba-satellite-a135-s4467/4507-3121_7-32327256.html](http://reviews.cnet.com/laptops/toshiba-satellite-a135-s4467/4507-3121_7-32327256.html)
 
[http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine](http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine)
says> Note 3 : Intel 945 integrated video chipset does not take kindly to OpenGL. If your game crashes frequently, try not using OpenGL. 
 
I've seen A video on youtube that used compiz while playing WoW.
[http://www.youtube.com/watch?v=yTzMXiYrCsw&feature=related](http://www.youtube.com/watch?v=yTzMXiYrCsw&feature=related)
 
WineHQ AppDB 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549)
says > INTEL issues 
Unfortunately, Intel does not make its own drivers for their cards for Linux. Their Windows drivers aren't even that good to start with. 
For World of Warcraft to work properly, you need to look for an Open Source Intel Driver that gives you direct OpenGL rendering support. Most dristros will have already had a good driver implemented into the kernel, particularly Ubuntu. So you need not worry about it. 
There are no known Issues with Intel Cards, however, it should be expected that the FPS will be lower as the Intel chips are integrated and hence share their video memory with the computer's main RAM as well as makes use of extra processing from the CPU.

 
typing 
```
glxinfo | grep "direct rendering"
```
returns
```
direct rendering:Yes
```
 
being very new to linux I either don't have wine install correctly which I added the wine repository by the command line with:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```
 
and used synaptic graphics to double check. and I have 1.3.1 installed.
I ran winetricks and installed d3dx9(all the ones that were marked that way) to make sure that I had all of them installed for it. I turned off rotating cube to make sure that I didn't use up too much mem for it.
anything else I should do???
 
I made the preemptive choice of wiping vista off my laptop completely cause I was sick of it and installed mint 10 on it cause well everything just worked. Well wanting to try out WoW has caused a lil regrete (not much) and I am currently fighting(XP drivers) to get my dual booted XP/Mint 10 to install WoW. My goal is to get rid of my windows completely. Only reason that the xp went back on is to see if it's my laptop or linux not wanting to run WoW. If I can get my linux to have WoW on it windows will be gone from my life completely. I've posted this before in the Mint forum and in linuxforums.org. I figure more the spread of the question better the input on how to fix. Thanks in advance.

---

### Post by Shintek on 2010-12-19
Dont think too hard, simply ask the YouTube video uploader how he got it to work!

---

### Post by AllRadioisDead on 2010-12-19
Good luck getting WOW to run on intel graphics.

---

### Post by Lintnewbie on 2010-12-19
I'm trying to run it on my laptop, so I'm unable to upgrade the vid card. Thats also why I quoted WineHQ AppDB where it say I should have no problems. I've tried a few window programs to see if wine was the issue and it's not. the youtube video was done with ubuntu 7.x in 2007. So what am I doing wrong is my question? not enough memory or is it installed wrong?

---

### Post by AllRadioisDead on 2010-12-20
> **Lintnewbie said:**
> I'm trying to run it on my laptop, so I'm unable to upgrade the vid card. Thats also why I quoted WineHQ AppDB where it say I should have no problems. I've tried a few window programs to see if wine was the issue and it's not. the youtube video was done with ubuntu 7.x in 2007. So what am I doing wrong is my question? not enough memory or is it installed wrong?

The problem is that your laptops video card (or lack there of) is simply not powerful enough to run WoW in wine. To be quite honest, it would struggle with WoW on anything but low settings in Windows as well.

---

### Post by cwwilson721 on 2010-12-20
It's NOT that the vidcard/chip is not powerful enough to run WoW, it's because of a failure of Intel to implement opengl enough (chip AND driver).

The chip runs WoW ok-ish in windows using D3D, but FAILS opengl. 

So you can't use it in WoW/wine. (Especially since patch 4.x, when the graphics demands went WAY up)

Period.

---

