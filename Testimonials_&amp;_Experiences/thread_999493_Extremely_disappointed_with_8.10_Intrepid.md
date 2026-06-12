---
title: "Extremely disappointed with 8.10 Intrepid"
date: 2008-12-01
forum: Testimonials &amp; Experiences
---

### Post by ninjabob7 on 2008-12-01
Yesterday I attempted to reinstall Windows with the "restore CD" and it wiped my entire hard drive instead of only the Windows partition (which it had done in the past). No big deal, I thought, I backed up all the important stuff. I hadn't yet upgraded to 8.10, and I figured it was probably better to do a fresh install anyway.

Boy was I wrong.

I downloaded and burned the iso for Intrepid 64-bit and it appeared to install with no problems. When it came up into the new system, it never asked any configuration questions. My first priority was wireless. I have a Prism chipset, supposedly one of the best-supported on Linux. When I originally installed Ubuntu back at 6.10, I had to do an ugly hack involving shell scripts and deleting duplicate drivers. Unfortunately, 2 years later it hasn't been fixed. The helpful config utility kept adding a space to my essid, which caused it not to connect.

After I finally hacked the network into working, I turned to graphics. My hardware worked (sort of) with the default drivers, but that was it. No resolutions above 800x600, which means other stuff is impossible to configure as the "OK" button is off-screen. I downloaded the NVIDIA drivers from the official site (as the Ubuntu versions hadn't and still didn't work for me). It failed to compile, complaining about a "Xen" kernel and asking me to install a new one. Unfortunately, there aren't any others available.

I tried the free "nv" driver as a temporary solution. No luck. In previous versions, nv has worked flawlessly. Now it won't even let the system boot. In addition, there are no configuration tools in the menus, but Hardy had several.

Now I have to download another 700MB iso and use up another CD just so I can attempt to rebuild my Hardy system. I had somehow gotten the idea that Ubuntu is "user-friendly," but after this experience I'm fairly disillusioned. If 8.04 wasn't LTS, I might consider another distro, except that nothing else works as well as Ubuntu after the original setup hiccups.

Is anyone else disappointed with Intrepid? Does anyone else know how to solve these problems? I'd like to be on the newest release if possible, because I know somewhere down the road I'll need an app that isn't available on Hardy. As a long-time Linux user and 2-year Ubuntu user, I expected a lot better. I'm just glad I didn't upgrade and break my entire system.

---

### Post by Oxidize on 2008-12-01
I have used Ubuntu on and off since it went public, granted i never stuck with it untill today when i installed 8.10 and so far so good, sorry you have had so much trouble.

---

### Post by roshanjose on 2008-12-01
look you shouldn't blame any Open Source or Free Software for its bad functionality.

One reason why these problems can help is that you can fix these bugs and take the credit for being a part of the development.

You got 2 take things positively....

If you don't like to fix any bugs and work with a stable verison...do use 8.04 LTS......this will do it.....

OSS do have their own weaknesses.....ppl are expected to help around

---

### Post by PocketDog on 2008-12-01
I'll never know what 8.10 is like, although from the multitude of posts on here I could probably take a pretty accurate guess. I'll upgrade from Hardy when 10.04 comes along...

---

### Post by scouser73 on 2008-12-02
I'm sorry to hear that you've had a bad experience with 8.10, as for myself I can only say that I have found it to be excellent in many ways.

---

### Post by ninjabob7 on 2008-12-04
Heh, thanks for your sympathy. I was mostly just venting.
Well, I tried going back to 8.04 only to discover that it had only been working in the first place due to a strange bit of luck. At some point when I wasn't paying attention, the Ubuntu team removed the orinoco_pci driver that I need for my wireless. It had only been working because I hadn't updated my kernel in so long. Now after trying to fix it for several days I'm going back to 8.10 as low-graphics mode is way better than no network. Apparently it is possible (but difficult) to get NVIDIA working, and it is apparently impossible to get wireless working on 8.04.
I don't really hate Ubuntu, but I'm rather frustrated because it used to work and now it doesn't. Two years ago I would have downloaded another distro, but Ubuntu is much better than any other I've tried (once it's finally set up properly).
I'll post again when I get everything working.

---

### Post by solwic on 2008-12-04
> **PocketDog said:**
> I'll never know what 8.10 is like, although from the multitude of posts on here I could probably take a pretty accurate guess. I'll upgrade from Hardy when 10.04 comes along...

Ditto.  I'm sticking to the LTS releases...all the other ones seem to have more problems than they're worth.  

Though I kind of almost like the new themes in Ibex.  Just wish we could get past the brown/orange stuff.  I guess that's kind of the Ubuntu colors though....

Anyway, go LTS!  :)

---

### Post by magmon on 2008-12-04
I couldnt be happier with Ibex. It did take about 3 hours to find my wireless, but after that everything (but java...) was smoothe sailing.

---

### Post by wolfen69 on 2008-12-05
> **ninjabob7 said:**
> and it is apparently impossible to get wireless working on 8.04.


please re-phrase that to: "i find it impossible to get wireless working for *me*". many use wireless with 8.04 no problem.

if it was me, and the wireless was the only issue, i would pony up the money for a compatible wireless card. for a lifetime of freedom, it's worth it.

plus, i've never had the problems that you do. ubuntu has always "just worked" on most computers i've tried. don't feel bad because you have nonconforming hardware, just make it right. i know people that can't run vista. even though the sticker on the computer said: "Vista ready". give me a break. i see windows machines that are absolutely broken in pieces all the time. I make them whole again. i install at least a dual boot of whatever variety they want.

my customers love ubuntu and use it most of the time. it's more than ready.

---

### Post by ahepas on 2008-12-07
Same here. It seems like everything crashes in 8.10. Which are my problems? Well, my system cannot restart, nicotine+ freezes and consumes alot CPU power(70%), brasero doesn't work and when i start amule klogd opens after a while and comsumes all CPU power! To continue working with the system i have to kill klogd from the command line. 
8.10 IS buggy!

---

### Post by gb5757870 on 2008-12-07
Totally agreed.

On the one hand I feel guilty complaining as this software is entirely free.

On the other hand, Intrepid feels like it's such a step backwards. I've been using Ubuntu since Warty and don't recall the last release I had so many moments I wanted to tear my hair out. It started off badly with spending hours getting my fat partition mounted to the point where I could at least write to it and it's just been downhill since then.

And now the latest bug which others have reported too, is that Firefox and Thunderbird seems to crash randomly.

Either by co-incidence or maybe not, now my XP partition is totally buggered so will need to re-install. 

Thumbs down,

---

### Post by mal on 2008-12-07
> **ninjabob7 said:**
> After I finally hacked the network into working, I turned to graphics. My hardware worked (sort of) with the default drivers, but that was it. No resolutions above 800x600, which means other stuff is impossible to configure as the "OK" button is off-screen.

I know this doesn't help solve most of your problems, but if you right-click on the task-bar, you can move a window anywhere on the screen using the mouse.  You can then get to the button you need to press.  This might help a bit when trying to get your screen settings right.

Mal

---

### Post by ninjabob7 on 2008-12-08
Well, it's been a few days, but everything is back up and running under Intrepid. This time I did manage to get the network running with Ubuntu's Network Manager, but it still added that space occasionally. I switched it to a less hackish version of what I had (using ifupdown this time) so it works consistently and without logging into X. There is still a bug where my DNS servers get erased by Network Manager, but once I manage to turn it off that should go away.
Nvidia graphics, after a bit of googling, turned out to be an issue of installing the nvidia-glx-legacy package (which restricted drivers manager didn't do for me). This is probably better anyway as now I don't have to reinstall the drivers for every kernel upgrade, but I wish Ubuntu would have been a bit more helpful.

Basically my problems are solved, aside from the DNS issue which should be 5-minutes work. Still, all this manual configuration leads me to the conclusion that Ubuntu is not quite ready for the masses, or at least the masses with wireless cards and nVidia graphics. On the other hand, the masses probably couldn't configure wireless on Windows, so it's not really a big deal.
I'm rather disappointed that the Ubuntu team broke orinoco cards in 8.04LTS, considering that it was filed as a bug long before the release. At least they put it back, though.

The moral of the story: if you're doing a fresh install, Intrepid might be better. If you're upgrading, expect things to break.

---

### Post by NCLI on 2008-12-09
If Ubuntu was preinstalled on most systems, like Windows, the drivers would not be a problem. Average joe doesn't install his own OS, the real problem here is the low availibility of prebuilt Ubuntu boxes.

---

