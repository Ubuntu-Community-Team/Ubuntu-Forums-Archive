---
title: "Team Fortress 2 runs real laggy in Wine"
date: 2009-05-15
forum: Wine
---

### Post by Beezleray on 2009-05-15
Hello,
Under Vista, TF2 ran great with my hardware and specs, but with wine its laggy (and not because of my internet connection) there is an annoying white flash every few seconds And its just very jittery and slow, and this is running it under the lowest visual specs possible. Is there anything I can do to make it run any better?

Any help would be great!

Thanks.

---

### Post by u235sentinel on 2009-05-15
> **Beezleray said:**
> Hello,
Under Vista, TF2 ran great with my hardware and specs, but with wine its laggy (and not because of my internet connection) there is an annoying white flash every few seconds And its just very jittery and slow, and this is running it under the lowest visual specs possible. Is there anything I can do to make it run any better?

Any help would be great!

Thanks.

What version of Wine and Ubuntu are you running?

Also what video card?

I have 1.1.18-1.1.21 (depends on what I"m doing) with 8.04 and a Nvidia 9800GTX.

It works great except for the mic.  Not sure how to fix that one yet :/

---

### Post by Beezleray on 2009-05-15
> **u235sentinel said:**
> What version of Wine and Ubuntu are you running?

Also what video card?

I have 1.1.18-1.1.21 (depends on what I"m doing) with 8.04 and a Nvidia 9800GTX.

It works great except for the mic.  Not sure how to fix that one yet :/

Well I'm running Ubuntu 9.04 with Nvidia GeForce Go 7600 (I think).

It took me a while but I found out I'm using wine 1.0.1 (I guess I need an upgrade).

---

### Post by u235sentinel on 2009-05-15
> **Beezleray said:**
> Well I'm running Ubuntu 9.04 with Nvidia GeForce Go 7600 (I think).

It took me a while but I found out I'm using wine 1.0.1 (I guess I need an upgrade).

I would make sure you are running the proprietary drivers for Nvidia cards and try upgrading to a newer version of wine.  I know 1.0.1 is stable but I had latency issues with TF2 and CSS as well.  Upgrading to something above 1.1.15 seems to work better but I'm still seeing some lag now and then.

What's interesting is it happens only online and not locally setup servers I built for playing with the kids.  I'm wondering if there is something more I'm missing.  But at least this improved things a lot.  Instead of red or yellow for my fps I'm in the green almost all the time now AND I've gone from 30-50 fps average to around 200 average :D

Just by upgrading to a newer version of wine.  It was amazing!

---

### Post by asdfoo on 2009-05-15
make sure you have OffscreenRenderingMode set to fbo too

open regedit, HKLM, Software, Wine, create a key called Direct3D, inside create a string entry called OffscreenRenderingMode and set the value to fbo.

---

### Post by MaLaCoiD on 2009-05-16
I was having a similar problem just now. I was getting like 10 fps with all settings on low and 1024x768 windowed mode. I'm using Compiz, so have the proprietary Geforce 8800 GT drivers in use.

I tried asdfoo's suggestion of adding OffscreenRenderingMode, but it didn't make a difference.

I'm now at 50-60 fps by upgrading Wine to 1.1.21. Thanks, u235sentinel.

You can add the dev-builds of Wine to Synaptic by following these [steps]("http://www.winehq.org/download/deb") for Jaunty:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by asdfoo on 2009-05-16
> **MaLaCoiD said:**
> 

I tried asdfoo's suggestion of adding OffscreenRenderingMode, but it didn't make a difference.


I meant do this in addition to upgrading to the latest beta.

---

### Post by u235sentinel on 2009-05-18
Thanks for the tip.  I've give that a try tonight.

---

### Post by u235sentinel on 2009-05-18
> **MaLaCoiD said:**
> I was having a similar problem just now. I was getting like 10 fps with all settings on low and 1024x768 windowed mode. I'm using Compiz, so have the proprietary Geforce 8800 GT drivers in use.

I tried asdfoo's suggestion of adding OffscreenRenderingMode, but it didn't make a difference.

I'm now at 50-60 fps by upgrading Wine to 1.1.21. Thanks, u235sentinel.



My pleasure.  Might want to try turning off compiz also.  I had issues with that until I turned it off.  Then things starting flying around 200+ fps

See if that helps a little more :-)

---

### Post by Gothamite on 2009-05-18
You might want to make sure visual effects are off, they caused some weird visual problems for me in games. This probably won't help, but I might as well just post it any way ;).

---

### Post by homerguy on 2009-05-19
My team fortress 2 is also laggy under wine but i have 1.1.21. It runs fine under xp with medium settings at 1024 x 768. But in wine I can hardly run it at all low settings. 

My Specs:
Ubuntu 9.04
Nvidia Geforce 6800 (using the nvidia 180 drivers from their site)
2.0 ghz amd 3200 processor
2gb of ram

---

### Post by Devilman13 on 2009-05-21
**I added -dxlevel 81 to the launcher options in Steam and noticed a HUGE improvement**... it plays just as smooth as it did on Windows for me. Without that option.. even if I turn down all my settings, I end up with slide shows during times of heavy action. :cool:

---

### Post by blithen on 2009-06-28
> **Devilman13 said:**
> **I added -dxlevel 81 to the launcher options in Steam and noticed a HUGE improvement**... it plays just as smooth as it did on Windows for me. Without that option.. even if I turn down all my settings, I end up with slide shows during times of heavy action. :cool:
How do you do that? Im still having extreme amount of lag.

---

### Post by mach-schnell on 2009-06-29
Launch steam, go to "My Games" tab, right-click on Team Fortress 2, and select "Set Launch Options."  Paste in "-dxlevel 81" and you should be set.

---

### Post by Devilman13 on 2009-11-10
In the end, I still got fed up with my framerates and terrible lag so I'm back to playing this on Windoze.

---

### Post by beastrace91 on 2009-11-10
> **Devilman13 said:**
> In the end, I still got fed up with my framerates and terrible lag so I'm back to playing this on Windoze.

Hehehe, weak hardware >.< - I snag round 50fps average on this one.

~Jeff

---

### Post by Devilman13 on 2009-11-17
....

It's a dual core P4 @ 3.0ghz, 4 gigs DDR3 ram, and an Nvidia Geforce 9500 w/ 1gig RAM *shrug*

---

### Post by joeelmex on 2009-11-17
Geforce 9500 is not a gamers card to begin with.  ??   I think a 9600 GT is the lowest I would ever recommend.

---

### Post by phreakyo on 2009-11-17
> **joeelmex said:**
> Geforce 9500 is not a gamers card to begin with.  ??   I think a 9600 GT is the lowest I would ever recommend.

It's far more than enough to run TF2, considering I run it on a 7800 Go laptop card with no issues.

---

### Post by beastrace91 on 2009-11-17
9500 is indeed a weak card.

And as stated - it takes a bit more horse power to run TF2 at a decent frame rate under Wine than it does on Windows.

~Jeff

---

### Post by joeelmex on 2009-11-17
> **phreakyo said:**
> It's far more than enough to run TF2, considering I run it on a 7800 Go laptop card with no issues.

Actually no, Sorry to say your Card is faster then his 9500.  

If you look at your specs, at 

[http://www.nvidia.com/page/go_7800gtx.html](http://www.nvidia.com/page/go_7800gtx.html)

The basic 7800Go, has a memory interface of 256 bit which gives you a memory bandwidth of 35.2 GB a sec.  

Unlike his 9500 

[http://www.nvidia.com/object/product_geforce_9500gt_us.html](http://www.nvidia.com/object/product_geforce_9500gt_us.html)

I am going to give him the 9500 GT (there is also a stand alone version with DDR 2 which is even slower then the GT labeled as a 9500)

The 9500Gt has a memory interface of 128 bit (Half of what you have) which gives him a bandwidth  of 25.6 GB a sec, or 16 GB a sec for the plain vanilla 9500 model. 

I think the problem is the transfer between the video card processor and memory it's being limited by his 128 bit bus.

His processor of the video could be 100 times fasters then your laptop but if it can only transfer a certain amount to the memory and back, thats the bottle neck.  Now in windows he might be able to play fine because he is not taking the hit of running a windows game in linux but in Linux we usually take a hit.

---

### Post by beastrace91 on 2009-11-17
@Joel If you look at this post you will see it is a 7800 GO card. Laptop cards are more than a little bit weaker than their desktop counter parts.

~Jeff

---

### Post by joeelmex on 2009-11-17
Jeff if you go to the link I posted it is for the 7800Go and the 9500 is for the desktop version.

His 7800Go is faster then the 9500.

---

### Post by beastrace91 on 2009-11-17
Ahh, alrighty - my mistake.

~Jeff

---

### Post by Devilman13 on 2009-11-19
The 9500 was all I could afford :cry:

But at least it was a step above a 9400 I had.

---

### Post by Notandi on 2009-11-19
Fresh install, 9.10 64bit, updated, installed Wine beta, installed steam. DL TF2 and its a slideshow and the menus looks screwed up. 

Tried the following launch options along with lowering graphics. 

-dxlevel 81 / -gl / -heapsize 1048576

The game is smooth under XP. C2D 6400, 3GB, NVidia 9800GTX+

What to do, oh wise ones?

---

### Post by joeelmex on 2009-11-19
Do you have any Desktop effects enabled Notandi?  Your computer should be able to run that fine, only thing I can think of is that your have desktop effects enabled.

---

### Post by beastrace91 on 2009-11-19
> **Notandi said:**
> What to do, oh wise ones?

IMO desktop effects shouldn't cause THAT much issue - at worse they should hurt your FPS by a small bit.

What driver version do you have installed? Also can you confirm it is the latest Wine version ```
wine --version
``` If this is indeed at the latest version (1.1.33) then try removing this version and installing a [past revision](http://wine.budgetdedicated.com/archive/index.html) - I know sometimes there are regressions on some hardware for people (personally I've had good luck with TF2 on Wine 1.1.28, .29, and .32)

Regards,
~Jeff

---

### Post by Notandi on 2009-11-22
Thx for the suggestions. Im not going to be playing for the next few weeks so Im putting this on ice.

---

