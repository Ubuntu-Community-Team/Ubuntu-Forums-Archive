---
title: "Wine and Steam Games"
date: 2009-09-06
forum: Wine
---

### Post by Buuntu on 2009-09-06
I haven't had any luck so far with getting steam games to work on Wine.  Steam starts up fine, but when I go to play any game, everything becomes incredibly slow and eventually crashes.  I've installed the mstcorefonts, is there anything else I need to do?

Video card = Nvidia 7300 GS and I have installed the recommended proprietary drivers for it.

---

### Post by bapoumba on 2009-09-06
Moved to Wine.

---

### Post by castlefox on 2009-09-06
What version of Wine are you using?

What steam games are you playing?

---

### Post by Buuntu on 2009-09-06
Wine version is 1.01.  The games I have tried are basically all the games using the half life 2 engine.  I think I've tried half life 2, portal, and counter strike source and all of them crashed.

---

### Post by castlefox on 2009-09-06
Ya.... You will want to move to a later development version of wine.  The development version is up to 1.1.29

---

### Post by Bonzai11 on 2009-09-06
Those games span across 3 different versions of the source engine.
HL2 is the original Css uses an upgraded pre Ojbox version,
and Portal uses the orange box engine also called source 2007.
They are for the most part different. Check the winehq for each of the games you want to play.
A wine version that works for one doesn't mean they work for all, well atleast for me thats how it works.

---

### Post by Buuntu on 2009-09-06
So I installed version 1.1.9 but now I can't see the fonts.  I copied over all Microsoft fonts to the appropriate folder but still nothing.  Anyone know how to fix that? :P

Can't test the game if I can't see it ^^.

---

### Post by castlefox on 2009-09-07
You cant see the font in/of what?  The font in the steam window? 
Or the WINE font?

---

### Post by Buuntu on 2009-09-07
I can't see any of the fonts in the steam windows.

---

### Post by bear24rw on 2009-09-07
I can run CS:S in wine i need to set hl2.exe to run in win98 mode though

using the package wine1.2

---

### Post by beastrace91 on 2009-09-07
I run CSS/TF2 through Wine and I've found that to get the best results you should do the following:

Make sure you have the latest release of Wine installed - sometimes there are regressions but for the most part newer releases always give better performance.

Install the latest nVidia drivers - updating to the latest 190.xx beta drivers gave me an almost 20 fps boost in CSS

When you run your games edit the launch options and set "-dxlevel 81" this drastically improves FPS

~Jeff

---

### Post by fsleeman on 2009-09-08
I am also having speed problems with wine. My system is:

AMD 64 3000+
nVidia 7900GS
ASUS k8v-vm motherboard
1 GB RAM

190.32 nVidia driver
ubuntu 9.04 64-bit
wine 1.1.29

I am getting about 15-35 FPS when playing TF2 at 1024x768 with all of the minimum settings. At this frame rate the game is only marginally playable and looks awful. Most of there parts are from my previous desktop which if I remember correctly, easily ran Steam games for years. I am launching the game with this script:

#!/bin/bash
WINEDEBUG=fixme-all nice -19 wine C:/Program\ Files/Steam/Steam.exe \
    -width 1024 -height 768 -applaunch 440 \
    -enable-opengl -dxlevel 81

Any suggestions?

---

### Post by beastrace91 on 2009-09-08
There really isn't terribly much I've found that speeds up TF2 other than the small increase you get from running it @ -dxlevel 81 at the moment Wine has only come so far and the performance hit is just something you kinda have to deal with. My 260m only runs between 30-50 on average.

Also just as an FYI I've noticed that tanking the gfx settings beyond normal really doesn't increase FPS more than a couple of frames.

~Jeff

---

### Post by fsleeman on 2009-09-08
I have read multiple claims that wine for steam games is just as fast or within 10-20% of the frame rate. Obviously some people here are seeing different results. So whats the reality of the situation? Do some steam games run well and others not?

I have a 260 and get more frames than I need at 1920x1200 and all settings on, wine must really be having a problem with TF2.

On a side note, I was trying to run Lost Coast to get a proper benchmark but wasn't able to get the test to work. The top and bottom Ubuntu desktop bars didn't go away, the mouse seemed to be offset by a little bit, and the game locked up when I actually tried to start the test. Has anybody been able to run this and if so, how did the results compared to windows?

---

### Post by beastrace91 on 2009-09-08
I have never noticed a performance increase in any Wine game (and I do all my gaming on Ubuntu) Alot of the time you can get near the same performance with lower settings but as I said I have not found anything that makes it the case with TF2. 

Perhaps some older games see a boost but other than Starcraft on occasion I really don't play anything older than CSS

~Jeff

---

### Post by castlefox on 2009-09-09
fsleeman maybe you should think about submitting a test for Lost Coast.  

The last submission was a long time ago.  It would probably help the wine project if more people would submit test results. Read up how to submit your test properly to the project if you bother doing so.  

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5729&iTestingId=13199](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5729&iTestingId=13199)

---

### Post by fsleeman on 2009-09-09
Sounds like a good idea, I am sure a lot has changed in a year. I'll try to make a post this week.

---

### Post by YokoZar on 2009-09-09
> **Buuntu said:**
> So I installed version 1.1.9 but now I can't see the fonts.  I copied over all Microsoft fonts to the appropriate folder but still nothing.  Anyone know how to fix that? :P

Can't test the game if I can't see it ^^.
Why did you install 1.1.9?

---

### Post by murderslastcrow on 2009-09-10
Yeah, there are some games that need twice the original RAM to play well, and some that can be grossly underestimated and still work. It all depends on the application, really.

Also, just because Steam works certainly does not mean the games in Steam will work. It's almost just as if you were playing the executable by itself without the launching program. Some Steam games work better without Steam.

---

### Post by lolman on 2009-10-06
I found my probelem (same as yours) solved by installing this browser engine

[http://gwos.org/doku.php/wine:steam](http://gwos.org/doku.php/wine:steam)

Hope it solves your probelem to.

---

### Post by RoBsTeR69 on 2011-01-03
> **Buuntu said:**
> I haven't had any luck so far with getting steam games to work on Wine.  Steam starts up fine, but when I go to play any game, everything becomes incredibly slow and eventually crashes.  I've installed the mstcorefonts, is there anything else I need to do?

Video card = Nvidia 7300 GS and I have installed the recommended proprietary drivers for it.
hi im new here but i know this video card i have the gigabyte 512mb version this particular card has a feature called "turbo cache"which I'm sure is good for "video" is no good for 3D stuff like games over a certain specification due to its design, it "borrows ram from system under load ,which seems to be what you are describing, i found this>>

[LIST]
[*] **Graphics Card Performance**  This  card's graphics processor and memory mean that it is not recommended  for most games, but it will still be fine for office applications and  other normal computing tasks.                                                      on this webpage>>         [http://reviews.cnet.com/graphics-cards/gigabyte-gv-nx73g128d-rh/1707-8902_7-31877486.html](http://reviews.cnet.com/graphics-cards/gigabyte-gv-nx73g128d-rh/1707-8902_7-31877486.html)  although this is not the original page i saw before ditching my card for a 250gts its the ram sharing that sucks with gaming me thinks hope this helps :)                                      
[/LIST]

---

