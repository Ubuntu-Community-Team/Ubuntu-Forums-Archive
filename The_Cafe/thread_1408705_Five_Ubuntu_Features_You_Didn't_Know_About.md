---
title: "Five Ubuntu Features You Didn't Know About"
date: 2010-02-16
forum: The Cafe
---

### Post by togo59 on 2010-02-16
Inspired by [ [COLOR="RoyalBlue"]_this blog_[/COLOR] ]("http://feedproxy.google.com/~r/LinuxMagazine/~3/Z0BCqYd811g/"), I thought I'd venture some of my own:

[LIST=1]
[*]Ubuntu chooses ALSA which has dropped support for common sound cards. If this affects you it's back to Windows for any music applications. Because so much depends on ALSA, if you junk it a whole stack of sound applications may as well be uninstalled.
[*]Ubuntu promulgates the ALSA myth that OSS is deprecated, which is a lie but nevertheless good advice: You actually have to pay for OSS. OSS works better for me than ALSA but you DO NOT get support, no matter how many times you write, and there's no MIDI capability.
[*]Wireless DOES NOT work with some (modern) LinkSys (Broadcom) wireless network cards. (Check how long I've been part of this hallowed circle, when I say it doesn't work, I mean precisely that.)
[*]Support for recent graphics cards (e.g. Radeon) is very patchy with Karmic.
[*]Ubuntu is free unless of course you consider your own time to be valuable in some way. If all the hours I've wasted is replicated in some small way across the rest of the community, the cost to the global economy must be huge.
[/LIST]

FYI:
My Toshiba laptop has the most successful Ubuntu installation ("just" needed bespoke AMD drivers to stop the black screen of death after Karmic was loaded).

My home PC (64bit) is the next worst, it's fine but useless for sound apps and that fault is the sole reason I have to keep XP alive. 

My daughter's Viglen box is the worst. For years (literally) I've been trying to figure out how to get her wireless card to work (almost identical card to mine) -- it just doesn't under Ubuntu -- fine under XP.

Any more features?

---

### Post by Twitch6000 on 2010-02-16
Nice find all of it is right. Execpt I thought ubuntu is now using pulseaudio <.<.

---

### Post by FuturePilot on 2010-02-16
> **Twitch6000 said:**
> Nice find all of it is right. Execpt I thought ubuntu is now using pulseaudio <.<.

PulseAudio does not replace ALSA.

---

### Post by speedwell68 on 2010-02-16
> **togo59 said:**
> Ubuntu is free unless of course you consider your own time to be valuable in some way. If all the hours I've wasted is replicated in some small way across the rest of the community, the cost to the global economy must be huge.


If I could install and configure Windows (XP or W7) in the same time I could install Ubuntu in the world would be a better place.

FYI: I have installed Ubuntu on a myriad of different machines Toshibas, Acers, Dells, HPs, Advents, Sonys and even a Mac and have never had any serious issues with any hardware.  The only issue I am currently having is getting my Uncle's Samsung C3050 phone to talk to his Linux Mint box.  The Mint Box talks to the phone but the Phone won't talk back, but then I have only spent about 10 minutes on the problem and phones don't like me.

---

### Post by matthew on 2010-02-16
> **Twitch6000 said:**
> Nice find all of it is right. Execpt I thought ubuntu is now using pulseaudio <.<.

PulseAudio is a sound server that sits on top of ALSA. They are both being used in Ubuntu.

[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

---

### Post by nrs on 2010-02-16
> **Twitch6000 said:**
> Nice find all of it is right. Execpt I thought ubuntu is now using pulseaudio <.<. No. PulseAudio is just a sound server. It still needs ALSA or OSS to provide infrastructure / drivers.   Here's good diagram.   [http://upload.wikimedia.org/wikipedia/commons/0/00/Pulseaudio-diagram.svg](http://upload.wikimedia.org/wikipedia/commons/0/00/Pulseaudio-diagram.svg)  Edit: wow beaten.

---

### Post by blur xc on 2010-02-16
> **togo59 said:**
> Inspired by [ [COLOR=RoyalBlue]_this blog_[/COLOR] ]("http://feedproxy.google.com/%7Er/LinuxMagazine/%7E3/Z0BCqYd811g/"), I thought I'd venture some of my own:

[LIST=1]
[*]Ubuntu chooses ALSA which has dropped support for common sound cards. If this affects you it's back to Windows for any music applications. Because so much depends on ALSA, if you junk it a whole stack of sound applications may as well be uninstalled.
[*]Ubuntu promulgates the ALSA myth that OSS is deprecated, which is a lie but nevertheless good advice: You actually have to pay for OSS. OSS works better for me than ALSA but you DO NOT get support, no matter how many times you write, and there's no MIDI capability.
[*]Wireless DOES NOT work with some (modern) LinkSys (Broadcom) wireless network cards. (Check how long I've been part of this hallowed circle, when I say it doesn't work, I mean precisely that.)
[*]Support for recent graphics cards (e.g. Radeon) is very patchy with Karmic.
[*]Ubuntu is free unless of course you consider your own time to be valuable in some way. If all the hours I've wasted is replicated in some small way across the rest of the community, the cost to the global economy must be huge.
[/LIST]

FYI:
My Toshiba laptop has the most successful Ubuntu installation ("just" needed bespoke AMD drivers to stop the black screen of death after Karmic was loaded).

My home PC (64bit) is the next worst, it's fine but useless for sound apps and that fault is the sole reason I have to keep XP alive. 

My daughter's Viglen box is the worst. For years (literally) I've been trying to figure out how to get her wireless card to work (almost identical card to mine) -- it just doesn't under Ubuntu -- fine under XP.

Any more features?


Wow- Promulgate and deprecate...

Does anyone else wonder why some words exist, when there are common every day words that mean the exact same thing?

Let me just say that they should come up w/ a different acronym for Open Sound System...  At first read, I interpreted OSS for Open Source Software, which lead to a lot of confusion with regards to the meaning of your point w/ the big words.

BM

---

### Post by Twitch6000 on 2010-02-16
> **matthew said:**
> PulseAudio is a sound server that sits on top of ALSA. They are both being used in Ubuntu.

[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

Oh okay thanks for that info :).

@everyone else correcting me I get it darn it lol..

---

### Post by Woolio1 on 2010-02-16
> **steveneddy said:**
> AMD, Broadcom and ALSA, the three things that don't work well under Linux due to the mfgr's and not the Linux community, and you choose to use all three and complain when there is ample evidence that it is hard to use.

Users who continue to use poorly supported hardware or software are doomed to posting threads telling everyone how much Linux and Ubuntu can do so much better.

Actually purchasing and using supported hardware from the beginning will solve so many issues and shut most of the mouth breathers up. I'm so tired of the threads about this that it makes me scream sometimes.

The same one's when you suggest system76 or ZaReason for a laptop or desktop with supported hardware start saying that it is so expensive. Give me a break, will ya?

Either run the supported hardware and stop b****ing or put up with the fixes that the community has developed and get on with your life.

Please.


Quoted for truth.

---

### Post by nrs on 2010-02-16
> **togo59 said:**
> Inspired by [ [COLOR=RoyalBlue]_this blog_[/COLOR] ]("http://feedproxy.google.com/%7Er/LinuxMagazine/%7E3/Z0BCqYd811g/"), I thought I'd venture some of my own:

[LIST=1]
[*]Ubuntu chooses ALSA which has dropped support for common sound cards. If this affects you it's back to Windows for any music applications. Because so much depends on ALSA, if you junk it a whole stack of sound applications may as well be uninstalled.
[*]Ubuntu promulgates the ALSA myth that OSS is deprecated, which is a lie but nevertheless good advice: You actually have to pay for OSS. OSS works better for me than ALSA but you DO NOT get support, no matter how many times you write, and there's no MIDI capability.
[*]Wireless DOES NOT work with some (modern) LinkSys (Broadcom) wireless network cards. (Check how long I've been part of this hallowed circle, when I say it doesn't work, I mean precisely that.)
[*]Support for recent graphics cards (e.g. Radeon) is very patchy with Karmic.
[*]Ubuntu is free unless of course you consider your own time to be valuable in some way. If all the hours I've wasted is replicated in some small way across the rest of the community, the cost to the global economy must be huge.
[/LIST]

FYI:
My Toshiba laptop has the most successful Ubuntu installation ("just" needed bespoke AMD drivers to stop the black screen of death after Karmic was loaded).

My home PC (64bit) is the next worst, it's fine but useless for sound apps and that fault is the sole reason I have to keep XP alive. 

My daughter's Viglen box is the worst. For years (literally) I've been trying to figure out how to get her wireless card to work (almost identical card to mine) -- it just doesn't under Ubuntu -- fine under XP.

Any more features?
Ignoring the obnoxious sarcasm; Which drivers have been deprecated? How old are they? 

Ubuntu promulgates the myth that OSS is dead simply because it does not use it? That's basically saying "if you're not with us, you're against us." It's insane. 

You'd think Linksys or Broadcom hardware would be Linksys'/Broadcom's problem. Same with ATI/AMD. If your hardware doesn't work, look I don't blame you, don't use Ubuntu if it doesn't work. But I think finger pointing at the kernel devs is misplaced, because they're essentially trying to fix someone else's problem. 

I have not wasted any time with Ubuntu or Linux in general because I had the foresight to pick hardware which was known to work. What you're doing essentially akin to purchasing Windows 7 and then whining when doesn't run on your PPC Mac.

---

### Post by Woolio1 on 2010-02-16
> **nrs said:**
> Ignoring the obnoxious sarcasm; Which drivers have been deprecated? How old are they? Ubuntu promulgates the myth that OSS is dead simply because it does not use it? That's basically saying "if you're not with us, you're against us." It's insane. You'd think Linksys or Broadcom hardware would be Linksys'/Broadcom's problem. Same with ATI/AMD. If your hardware doesn't work, look I don't blame you, don't use Ubuntu if it doesn't work. But I think finger pointing at the kernel devs is misplaced, because they're essentially trying to fix someone else's problem. I have not wasted any time with Ubuntu or Linux in general because I had the foresight to pick hardware which was known to work.

I haven't wasted time because I tinker with it, and find it fun to try and fix something when it breaks.

That cheap netbook was the best PC purchase I've made in a long time...

---

### Post by Megrimn on 2010-02-16
meh.  The only computer I'm having problems with is my dad's presario 1200us laptop, and that's because the hardware is extremely dated and it has no lan port or wireless with which to update the system. (I'm trying to fix the internet problem via the cardbus.) It's a tough little thing though - we found it on the side of the road and save for the optical drive, everything functions.

---

### Post by ElSlunko on 2010-02-16
+1 for the creative rant. For a second I thought it was going to be a thread about cool easter eggs inside Ubuntu.

---

### Post by chillicampari on 2010-02-16
> **steveneddy said:**
> ...

Actually purchasing and using supported hardware from the beginning will solve so many issues and shut most of the mouth breathers up. I'm so tired of the threads about this that it makes me scream sometimes.

...

Please.

It's a great idea to purchase supported hardware, but what about regressions?


[http://www.workswithu.com/2009/05/06/the-ubuntu-904-intel-graphics-fiasco/](http://www.workswithu.com/2009/05/06/the-ubuntu-904-intel-graphics-fiasco/)
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by gsmanners on 2010-02-16
> **togo59 said:**
> ...you consider your own time to be valuable in some way.

I've never really understood this mentality. How precisely is time valuable? Time itself isn't a commodity you can give or take, and inherently time doesn't even really have any meaning (outside its inverse proportional relationship to energy divided by mass, of course).

I suppose it's a cultural phenomenon, but I wonder if there is any foundation in nature. I find it hard to believe that there is one.

---

### Post by Mahngiel on 2010-02-16
> **steveneddy said:**
> AMD, Broadcom and ALSA, the three things that don't work well under Linux due to the mfgr's and not the Linux community, and you choose to use all three and complain when there is ample evidence that it is hard to use.
 
Users who continue to use poorly supported hardware or software are doomed to posting threads telling everyone how much Linux and Ubuntu can do so much better.
 
Actually purchasing and using supported hardware from the beginning will solve so many issues and shut most of the mouth breathers up. I'm so tired of the threads about this that it makes me scream sometimes.
 
 
While this is a great perspective from somebody who knew yesterday they would run linux tomorrow, you can only hopelessly expect every convert to do the same.  To blashpemize them based on the fact that did not but 100% supported hardware before they even knew they wanted to try linux, or even *heard* of linux for that matter, is a sham.
 
If it pains you so much to assist others' blights perhaps you are in the wrong type of community.  And completely off of Ubuntu's general philosophy.

---

### Post by ElSlunko on 2010-02-16
> **gsmanners said:**
> I've never really understood this mentality. How precisely is time valuable? Time itself isn't a commodity you can give or take, and inherently time doesn't even really have any meaning (outside its inverse proportional relationship to energy divided by mass, of course).

I suppose it's a cultural phenomenon, but I wonder if there is any foundation in nature. I find it hard to believe that there is one.

This applies only if you spend time you would be utilizing to make money on fixing an Ubuntu install. Most people don't make money every waking moment of their lives. It's an over dramatization of a possible problem.

---

### Post by MooPi on 2010-02-16
The best and simplest way to get a computer to work perfectly with Ubuntu is to buy a system preloaded. Dell, System76 just to name a couple. The second best way is to build your own and research the components that are known to function well with Linux. I build my own and rarely have issues with components. Last time I had an issue it was my fault and not Ubuntu's.

---

### Post by togo59 on 2010-02-18
> **nrs said:**
> Ignoring the obnoxious sarcasm; Which drivers have been deprecated? How old are they? 

Ubuntu promulgates the myth that OSS is dead simply because it does not use it? That's basically saying "if you're not with us, you're against us." It's insane. 


_nrs_: Perhaps you'll rethink your obnoxious accusation when you've read this. [Ubuntu.com Community OpenSound]("https://help.ubuntu.com/community/OpenSound")

Admittedly, I have wasted hours with Windoze (and other operating systems). Certainly XP and its ancestors had me vexed (if that's not too long a word) on occasion. ;) 

But hey, I still use Ubuntu.

And did I mention setting up a VPN? Unfortunately vpnc didn't quite do it for me (doesn't appear to support TCP tunnelling) so I have to compile the Cisco sources. But I only spent an afternoon on this so I'm not done yet.

---

### Post by SuperSonic4 on 2010-02-18
> **togo59 said:**
> _nrs_: Perhaps you'll rethink your obnoxious accusation when you've read this. [Ubuntu.com Community OpenSound]("https://help.ubuntu.com/community/OpenSound")

Admittedly, I have wasted hours with Windoze (and other operating systems). Certainly XP and its ancestors had me vexed (if that's not too long a word) on occasion. ;) 

But hey, I still use Ubuntu.

And did I mention setting up a VPN? Unfortunately vpnc didn't quite do it for me (doesn't appear to support TCP tunnelling) so I have to compile the Cisco sources. But I only spent an afternoon on this so I'm not done yet.

Your post lost all credibility after mentioning "Windoze" *[sic]*


It is fair what the OP says although I think the title should be "Five Ubuntu features Canonical doesn't want you to know". 

This is getting more and more important since many people are thinking ubuntu is the *only* distro out there (search for something like "ubuntu doesn't work ... back to windows")

---

### Post by togo59 on 2010-02-18
> **gsmanners said:**
> I've never really understood this mentality. How precisely is time valuable? Time itself isn't a commodity you can give or take, and inherently time doesn't even really have any meaning (outside its inverse proportional relationship to energy divided by mass, of course).

I suppose it's a cultural phenomenon, but I wonder if there is any foundation in nature. I find it hard to believe that there is one.

My time IS a commodity. I give it to all sorts, whether it's charitable work, family time or work time. I never ever have enough of the damn stuff. If I spend the day fruitlessly trying to fix something, trawling through forums, installing this and that, compiling source code and all to no avail, I do feel cheated out of my time. Put simply, if I had more time I could earn more money.

BTW: The units of energy divided by mass are length squared divided by time squared. But that doesn't help understand time. Einstein's fourth dimension is one explanation of it but aside from relativistic dynamics it's better thought of as a space (albeit one-dimensional) that allows action. Without time nothing can happen. Different sentient beings might have quite different perceptions of time, but that's another matter. (Did I say "matter"? :D )

---

### Post by gsmanners on 2010-02-18
> **togo59 said:**
> Einstein's fourth dimension is one explanation of it but aside from relativistic dynamics it's better thought of as a space (albeit one-dimensional) that allows action. Without time nothing can happen. Different sentient beings might have quite different perceptions of time, but that's another matter. (Did I say "matter"? :D )

Einstein simplified: 2 + 2 = 5

I would say that without things happening, there can be no definition of time.

---

### Post by K.Mandla on 2010-02-18
> **togo59 said:**
> I thought I'd venture some of my own:

[LIST=1]
[*]Ubuntu chooses ALSA which has dropped support for common sound cards. If this affects you it's back to Windows for any music applications. Because so much depends on ALSA, if you junk it a whole stack of sound applications may as well be uninstalled.
[*]Ubuntu promulgates the ALSA myth that OSS is deprecated, which is a lie but nevertheless good advice: You actually have to pay for OSS. OSS works better for me than ALSA but you DO NOT get support, no matter how many times you write, and there's no MIDI capability.
[*]Wireless DOES NOT work with some (modern) LinkSys (Broadcom) wireless network cards. (Check how long I've been part of this hallowed circle, when I say it doesn't work, I mean precisely that.)
[*]Support for recent graphics cards (e.g. Radeon) is very patchy with Karmic.
[*]Ubuntu is free unless of course you consider your own time to be valuable in some way. If all the hours I've wasted is replicated in some small way across the rest of the community, the cost to the global economy must be huge.
[/LIST]
...
Any more features?
Those don't sound like features. They sound like thinly veiled rants.

---

### Post by donato roque on 2010-02-20
They're not thinly veiled in my humble opinion.
They are rants.
The blog the OP linked too is more satisfying to read though.  I would stop there.  There is nothing to redeem this thread.

---

### Post by Kenny_Strawn on 2010-02-20
> **togo59 said:**
> Wireless DOES NOT work with some (modern) LinkSys (Broadcom) wireless  network cards.

Actually, my WMP600N (a very new model, the Wireless N **Dual-band** PCI network adapter) works perfectly, and without NDISWrapper or any other aid. Even from the Live CD, no issues.

---

### Post by ElSlunko on 2010-02-20
We should make a thread about features that aren't obvious.

---

