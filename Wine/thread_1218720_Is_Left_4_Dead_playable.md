---
title: "Is Left 4 Dead playable?"
date: 2009-07-21
forum: Wine
---

### Post by ztmike on 2009-07-21
Has anyone here gotten Left 4 Dead playable on Ubuntu? Hopefully I'm not breaking any rules asking this?

---

### Post by Whiffle on 2009-07-21
Looks like it gets a Gold rating in WineHQ's AppDB for Ubuntu 9.04.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=8610](http://appdb.winehq.org/objectManager.php?sClass=application&iId=8610)

---

### Post by ztmike on 2009-07-21
Well I tried running it on high settings with full screen..and it was unplayable. Running on a 2.5ghz dual core 8800GT and 6gig ram. 

Wondering what kind of setting I need to set it at? I'm guessing from your link "Gold" means it runs good? ..not in my case then ..

Edit: Just noticed on that page, that it looks like they tested the game using .24 of Wine, I used .1 

Does the difference in versions actually let players play this game?

---

### Post by Whiffle on 2009-07-21
I just started it installing on mine, will report back whenever it gets done.

---

### Post by DEagleson on 2009-07-21
My little brothers Compaq CQ60 plays L4D quite good considered the slow hardware.

OS: Vista SP2
2.0 GHz Celeron
Intel GMA X4500mhd
2 GB Ram

But hes using Micro$low so since Ubuntu run like crap for him.

---

### Post by Whiffle on 2009-07-21
Its almost playable on mine.  The settings don't go as high, and gameplay is a bit choppy.  Maybe with tweaking it could be better.

Specs:
Ubuntu 9.04 64bit
9800GTX+ 1GB
E8400 C2D @ 3 ghz
4 gb ram

---

### Post by ztmike on 2009-07-21
Can you try using these settings?

[http://appdb.winehq.org/screenshots.php?iAppId=&iVersionId=14592](http://appdb.winehq.org/screenshots.php?iAppId=&iVersionId=14592)

---

### Post by Sand &amp; Mercury on 2009-07-21
Source engine games in general work ok, but performance depends hugely on your gfx card and drivers. For my Xpress200M chipset, using the radeon driver, Half Life 2 runs like a dog in wine, even on the lowest graphics settings (and with -dxlevel 70) while on Vista my frame rate rarely dropped below 30FPS on normal settings.

---

### Post by ericmc783 on 2009-07-21
> **mgandy said:**
> I have heard this game is pretty cool. I have yet to play it but I am hoping I get the chance soon.

It is VERY cool. One of the games I have on my Vista partition. 

Valve has announced a sequel, L4D2, due out in November, which has received much backlash from the gaming community, due largely in part to Valve's previous statements that L4D would have a long support life, and be given content updates over time.
 More info: [http://www.perezstart.com/microsoft/xbox360-microsoft/valve-receives-community-backlash-on-left-4-dead-2/6319/](http://www.perezstart.com/microsoft/xbox360-microsoft/valve-receives-community-backlash-on-left-4-dead-2/6319/)

---

### Post by joeelmex on 2009-07-22
I never got it to run in the latest version of it in wine stable enough for online. I play it everything max out on cedega online.

---

### Post by snargfish on 2009-07-22
I can't get it to work with Wine. :(

---

### Post by Sophont on 2009-07-28
I had no trouble getting it to run (up-to-date wine from winehq) on my laptop.

Only problem I have is that my old Nvidia 7900 GS (in laptop) overheats after a while. Without that I'd have no complaints.

Fun game :-)

---

### Post by Spectre5 on 2009-11-09
Has anyone gotten this game to run in full-screen?  I'm having no luck with that, though it seems to work OK in a window (a little laggy...).

Has anyone tried running this via virtualbox?  I was thinking about testing that out...

---

### Post by beastrace91 on 2009-11-09
It will not run via Virtual Box - VMs do not support any form of 3D acceleration.

As for Wine - even with every optimization setting under the sun on powerful hardware (nVidia 260m running 1gig DDR3 Dedicated RAM) I can only get L4D to run choppy at best via Wine/Codeweavers (around 25ish FPS in 1024x768 res). By comparison how ever Cedega runs L4D at around three times this speed for me (75ish on average) - so its more than playable on Ubuntu this way.

~Jeff

---

### Post by u235sentinel on 2009-11-09
I couldn't get the left 4 dead 2 demo working with crossover games.  But then again I did read that 8.0 wouldn't work (probably) until their next update is available.

Regular Wine probably would have similar problems though I've heard that Left 4 Dead 1 works great under Crossover Games and Wine.  Haven't bought it yet though with LFT2 coming out I"ll probably just wait :D

---

### Post by beastrace91 on 2009-11-09
L4D2 (demo) currently fails to load properly on Wine/CXGames/Cedega. Also L4D runs just as poorly under CXGames as it does under plain old Wine (it runs, but at a horrid frame rate like I said).

Also if you want to get them both there is a combo pack on Steam with both games that gets you a discount.

~Jeff

---

### Post by Spectre5 on 2009-11-09
YA, I have L4D installed (via WINE) and it works, but it definitely is not very smooth.  I turned the graphics way down to, which helped some.  Still not good enough for me to realistically play it though.

But for as a general exercise in WINE - how do I get this to run in full screen?  When I start the game, it is set to go to full screen, but it stays in a WINE window.  I think I have the configuration options for WINE Set correctly to allow full screen...

---

### Post by beastrace91 on 2009-11-09
You mean you are still seeing the top and/or bottom Gnome bars? Toggling Compiz off normally fixes this issue for most applications.

Also as an FYI if this is the issue does not exist when running L4D through Cedega ;)

~Jeff

---

### Post by joeelmex on 2009-11-10
I had that same issue and I have nice gaming laptop, so thats when I tried Cedega, and it runs very smooth over there.  I use cedega to play left 4 dead but unfortunately, left 4 dead 2 does not work. :(

> **Spectre5 said:**
> YA, I have L4D installed (via WINE) and it works, but it definitely is not very smooth.  I turned the graphics way down to, which helped some.  Still not good enough for me to realistically play it though.

But for as a general exercise in WINE - how do I get this to run in full screen?  When I start the game, it is set to go to full screen, but it stays in a WINE window.  I think I have the configuration options for WINE Set correctly to allow full screen...

---

### Post by beastrace91 on 2009-11-13
Hey All,

I've compiled a listing of benchmarks regarding L4D on Ubuntu for any interested - [http://jeffhoogland.blogspot.com/2009/11/wine-cedega-and-cxgames-benchmark.html](http://jeffhoogland.blogspot.com/2009/11/wine-cedega-and-cxgames-benchmark.html)

~Jeff

---

### Post by myromance123 on 2009-11-14
Reporting in.

 For L4D original, I can play singleplayer no probs. No special settings done to get it working. Check what I use below (only prob is with online play...yeah not cool).

 For L4D2 demo, I can definitely play it but I had to get a tar.gz from the appdb.wine site and extract that into L4D2's demos directory.

 Not that sluggish as people say, at least for me and my specs ( I use some pretty old stuff here).

OS: Ubuntu 9.10
Processor: Pentium 4 2.8GHz
RAM: 1.5GB DDR1
Graphics: Nvidia GeForce 9400GT (binary drivers 190.42)
WINE: ver 1.1.32  (yes the version matters. Older ones may work or suck)

 Good game but the second sucks cos of the character change :D

---

### Post by handy on 2009-11-14
I'm a tester for Codeweavers, & today I received an email stating that they have just produced a pre-release version of Crossover Games, that has been primarily built to support Left 4 Dead 2.

I haven't tested it, as I don't play the game.

I just thought that someone might like to know that they are on the job.

---

### Post by beastrace91 on 2009-11-14
> **myromance123 said:**
>  For L4D original, I can play singleplayer no probs. No special settings done to get it working. Check what I use below (only prob is with online play...yeah not cool).

What frame rate do you get and at what resolution and detail settings do you use? "Plays" and "plays well" are very different.

~Jeff

---

### Post by myromance123 on 2009-11-18
resolution has been tested on 1600x900 and 1240x768. Running everything on low, thats how I played it before and thats how I play it now (RAM aint enough for high and a pentium 4 cant handle that lawl).
 Never checked the framerate, but I'm using the latest Nvidia driver 190.42, makes a [COLOR="Red"]huge[/COLOR] difference. See for yourself.

:)

---

### Post by beastrace91 on 2009-11-18
> **myromance123 said:**
> latest Nvidia driver 190.42, makes a [COLOR="Red"]huge[/COLOR] difference.

Yep. I know this and I'm running this (been running the latest 190.xx driver since .25 came out). Wine still will not break 25ish FPS for me in the game. Which is lessthan smooth.

~Jeff

---

