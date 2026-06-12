---
title: "Frustration"
date: 2021-01-18
forum: Ubuntu, Linux and OS Chat
---

### Post by leif-s-o on 2021-01-18
Hello everyone!

Let me start with a little rant. I just encountered (once again) a bug where my Ubuntu 20.04 wasn't usable any more. It showed me only a black screen after boot. This time, it happened after following instructions from a website telling me step-by-step, how to enable a chinese keyboard.
This is unfortunately not the first time I encountered big problems with Ubuntu 20.04. I recently had issues with hardware, like a monitor or a Wacom-tablet not being recognized, and with software bugs in Xournal++ or in Kdenlive. Also, I am tired of trying out a bunch of different alternative programs just to realize in the end, that the program I was using all the time is probably the lesser evil.

And these things make me sad, because I love Ubuntu. I started using it 12 years ago as an alternative to Windows, and I always had - and still have - the feeling that using Linux is the right way.
But all these issues that i run into make me become more and more frustrated with Ubuntu.
What I want is a Ubuntu that just works and does not keep me from doing my stuff.
When I want a chinese keyboard, I want to install it with one click in the configurations of Ubuntu, and not by following a step-by-step manual that I found on the web, leading to an unusable system.
When I plug in a Wacom tablet, it should just work (unlike now, where it gives me a 50-50-chance of working or not working).

So, I am wondering:
Am I the only one in this state of loving and hating Ubuntu at the same time?
Do you also run into many issues with Ubuntu 20.04?
And what do you recommend me to do? Should I go back to 18.04?
Do you know any other Distros that make less trouble?
And in case you know: How to get a chinese keyboard (pinyin input) running on Ubuntu 20.04?

Ah, and to finish the story: After googleing on my smartphone for some time, I found out that I need to revert the input method back to IBus via terminal, so I could at least use my computer again, but I don't know how long it will still take me to successfully install a chinese keyboard, which is ridiculous, keeping in mind that Ubuntu is the OS that claims to stand for usability and accessibility more than any other system, and has been developed for such a long time. But I guess I won't be able to type my chinese homework this week, while my classmates using Windows have no issues. And I am just too busy to spend a whole afternoon solving these issues.

Cheers,
Leif

---

### Post by TheFu on 2021-01-18
Following random instructions from websites is a bad idea.  Nice rant.
Maybe stick with official documentation?  [https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by T6&amp;sfpER35% on 2021-01-18
> [COLOR=#000000]Do you also run into many issues with Ubuntu 20.04?[/COLOR]
nope not one issue

but then again , i haven't tried installing chinese lol

---

### Post by GhX6GZMB on 2021-01-18
My Lubuntu 20.04 is running beautifully and is 100% stable.

I have to agree with TheFu about following "web experts" who to 99% are totally clueless amateurs. Finding the 1% who know what they are talking about is unfortunately extremely difficult.

My system offers fcitx as input method manager, I don't know about Ubuntu.

---

### Post by grahammechanical on 2021-01-18
Why not dual boot with Ubuntu Kylin? Then you can get frustrated trying to install an English keyboard. :) Sorry, I just could not resist. But may be Ubuntu kylin is the answer.

[https://www.ubuntukylin.com/index.php?lang=en](https://www.ubuntukylin.com/index.php?lang=en)

It is an official Ubuntu flavour.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

Ubuntu itself does not frustrate me. Needing one or two non Linux apps and having difficulty getting them working. That frustrates me. Ever tried getting an Android app running on Linux? I succeeded but the app gets upgraded and I spent most of a day trying to install newer versions and they are crashing. With smartphones and tablets more powerful than my 13 year old desktop machine I get the feeling that this particular app has such increased functionality that my desktop machiine does not have the resources. Frustrated indeed.

Regards

---

### Post by mastablasta on 2021-01-19
adding keyboard needs video? in KDE you just go to system settings and add a keyboard and language. i've added US keyboard to my native one, so i can access tilde (console--> cheats :P ) in some wine games. and vice versa - i have US keyboard on a laptop i bought in Asia, and i would always add native keyboard, so i can type all the strange letters we use. i know where they are located by heart. 

also we have 
Kubuntu 18.04.1 on a very old PC since Jan 2019 - no issues so far. usage: internet browsing, some light gaming (old games through wine or on steam), server management
Kubuntu 18.04 with HWE kernel on new PC since Jan 2020 - works very good so far. no issues with the OS itself and i am very surprised at how few bugs i ran into. no major ones. usage: school (video conference), light video and photo editing, browsing, online school tasks, gaming (steam, proton, wine), moderating and administering website 
Kubuntu 20.04 LTS since June 2020- had some issues setting it up. patched kernel with wifi driver and added kernel parameter to avoid boot issue when on battery. since then no issue at all so far. usage:  school (video conference), browsing, online school tasks, gaming (steam, proton, wine)

the only thing that bothers me is that Kubuntu no longer offers 5 year LTS support.

---

### Post by Shibblet on 2021-01-22
> **leif-s-o said:**
> Hello everyone!

Let me start with a little rant. I just encountered (once again) a bug where my Ubuntu 20.04 wasn't usable any more. It showed me only a black screen after boot. This time, it happened after following instructions from a website telling me step-by-step, how to enable a chinese keyboard.
This is unfortunately not the first time I encountered big problems with Ubuntu 20.04. I recently had issues with hardware, like a monitor or a Wacom-tablet not being recognized, and with software bugs in Xournal++ or in Kdenlive. Also, I am tired of trying out a bunch of different alternative programs just to realize in the end, that the program I was using all the time is probably the lesser evil.

And these things make me sad, because I love Ubuntu. I started using it 12 years ago as an alternative to Windows, and I always had - and still have - the feeling that using Linux is the right way.
But all these issues that i run into make me become more and more frustrated with Ubuntu.
What I want is a Ubuntu that just works and does not keep me from doing my stuff.
When I want a chinese keyboard, I want to install it with one click in the configurations of Ubuntu, and not by following a step-by-step manual that I found on the web, leading to an unusable system.
When I plug in a Wacom tablet, it should just work (unlike now, where it gives me a 50-50-chance of working or not working).



I completely feel your pain.  There are a couple of issues that I have had to "come to grips" with when transitioning from Windows to Linux.  The first is, simply put, Windows has much better driver support for hardware.  Where Linux may support the HW in the Kernel, and there are ways to wrap drivers from Windows to work... ultimately direct drivers in Windows work better with their respective hardware.  For example, I have a Samsung 840 Pro SSD, and the Samsung Magician software will not work in Linux, it is Windows only.

The true freedom comes from running free software.  And the biggest problem people have with understanding this, is thinking that "all" software is free.  This unfortunately leads to people thinking that Ubuntu is just a free version of Windows, and will run all their non-free Windows software, freely...  I'm sure you can see the flaw in this logic.  The deeper flaw, is that even most Linux OS's aren't "free" to coin the FSF term.  Media (games, movies, music, books) is not "Free."  These things have usage fees, and they are part of the "licensing agreements" taken at purchase or run-time.  Just because you use Ubuntu, doesn't mean you get to pirate software in the name of freedom.

Freedom is the right to use software (run, alter code, add to, etc.) however you see fit.  But that software cannot be "non-free" to begin with.  You aren't allowed to alter Microsoft Edge (the old one) and turn it into your own browser.  However, the Chromium project, can be altered and turned into different browsers (New-Edge, Google Chrome, Brave, etc.) without cost.  But the parts added by each of the companies is, again, non-free software, making the end result non-free.  Chromium, however, unaltered, is still "free."

> **leif-s-o said:**
> 
So, I am wondering:
Am I the only one in this state of loving and hating Ubuntu at the same time?

No.  I do this all the time.  I love Kubuntu, and hate Kubuntu.  Driver issues, which are more of a "Linux as a whole" thing.  I buy a new piece of Hardware that suits my purpose very well, and lo-and-behold, it won't work in Linux.  So, I have Windows around for just this purpose.

Also, I have 20 years of work and training in Adobe Software.  I started with Aldus Photostyler and Aldus Pagemaker a long time ago, and progressively worked into Adobe Photoshop, Adobe Illustrator, and Adobe InDesign (previously Pagemaker).  And the "free" software available that works in a very similar way, just doesn't cut it for me.  GIMP, is a great Photoshop alternative.  Inkscape is a great Illustrator alternative.  Unfortunately, Scribus is a weak InDesign alternative, so I cannot use it.

> **leif-s-o said:**
> 
Do you also run into many issues with Ubuntu 20.04?

Not MANY, but Some.  Usually in the form of drivers.  Especially Nvidia.  But this was from previous versions.  With 20.04, everything really just seems to work well.

> **leif-s-o said:**
> 
And what do you recommend me to do? Should I go back to 18.04?

If it didn't have any problems for you, then sure, if you like.  I usually take the time to learn the new LTS version, and how to work out the issues I need worked out.  Most of which are resolved within a month of release.  If these issues are a problem for you, I would suggest only using the LTS (Long Term Support) releases, and not the interim ones.  i.e. 20.10

> **leif-s-o said:**
> 
Do you know any other Distros that make less trouble?
And in case you know: How to get a chinese keyboard (pinyin input) running on Ubuntu 20.04?

Yes, and No.

Ubuntu (and it's flavors), Mint, Pop!_OS, Zorin, and most Ubuntu based distros are the easiest ones for people to use.  Whether that's transitioning from Windows, or just giving "Linux" a try.  So, they make less trouble from a user interface point of view... but other distros like Fedora, Manjaro, PCLinuxOS, and the like can make less trouble from a technical standpoint.  Then there are distros like Gentoo and Arch that take more time to set up (sometimes people equate more time to mean more trouble), but can be the most stable systems in the long run.

But a Pinyan Keyboard... Sorry man, that one I just don't know.

> **leif-s-o said:**
> 
Ah, and to finish the story: After googleing on my smartphone for some time, I found out that I need to revert the input method back to IBus via terminal, so I could at least use my computer again, but I don't know how long it will still take me to successfully install a chinese keyboard, which is ridiculous, keeping in mind that Ubuntu is the OS that claims to stand for usability and accessibility more than any other system, and has been developed for such a long time. But I guess I won't be able to type my chinese homework this week, while my classmates using Windows have no issues. And I am just too busy to spend a whole afternoon solving these issues.

Cheers,
Leif

Good Luck to you.  And please never feel afraid to ask questions here!  We all try to help the best we can.

---

### Post by Shibblet on 2021-01-22
> **ml9104 said:**
> My Lubuntu 20.04 is running beautifully and is 100% stable.

I have to agree with TheFu about following "web experts" who to 99% are totally clueless amateurs. Finding the 1% who know what they are talking about is unfortunately extremely difficult.

My system offers fcitx as input method manager, I don't know about Ubuntu.

Ain't that the truth... Back with Kubuntu 18.04, I was having issues with the Nvidia drivers, and all of these crazy web-sites were showing how to piece-by-piece disable the Nouveau driver, and install the Nvidia drivers one module at a time.  After about a thousand "re-installs," I realized that I had forgotten about this forum... Then came herre, and found that all I had to do was "Blacklist" the Nouveau Driver, and install the Nvidia one.

It was like the clouds parted and sunshine came down from the heavens while a choir of angels chanted to my success.

---

### Post by TheFu on 2021-01-22
> **Shibblet said:**
>  Then came herre, and found that all I had to do was "Blacklist" the Nouveau Driver, and install the Nvidia one. 

In theory, running:

```
$ sudo ubuntu-drivers autoinstall
```

should handle that stuff automatically. My 20.04 system is only virtual, so I can't test it, but it does work on 16.04 and 18.04 as I recall.

---

### Post by Shibblet on 2021-01-22
> **TheFu said:**
> In theory, running:

```
$ sudo ubuntu-drivers autoinstall
```

should handle that stuff automatically. My 20.04 system is only virtual, so I can't test it, but it does work on 16.04 and 18.04 as I recall.

Even easier.  ;-)

---

### Post by zebra2 on 2021-01-24
No habla Chinese but I have three Lenovo Ideapads, one with 20.04, one with 20.10 and one with 21.04.  The only problem I've had is with the new printer installer which seems to be now working just fine. Also, one reinstall on the  21.04 but I invited  that by 1. running a development version and 2. having proposed enabled (but still do). Most of the problems I've had over the years were related to trying to force unsupported devices on the kernel. Even in those cases there was some pretty technical workarounds which I was able to use. Those old days are mostly gone.  The only problem I actually have currently is the single Windows 10 partition that I only use once a year at tax time. I takes more time to get it working than I spend on my taxes. So it's all good! Be happy!

---

