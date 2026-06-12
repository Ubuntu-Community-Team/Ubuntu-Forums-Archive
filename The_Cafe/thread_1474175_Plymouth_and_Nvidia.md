---
title: "Plymouth and Nvidia"
date: 2010-05-05
forum: The Cafe
---

### Post by -humanaut- on 2010-05-05
Seems like the Plymouth resolution problem with Nvidia is fixed after todays updates. Thought I would let everyone know because this has been a nagging problem.

---

### Post by murderslastcrow on 2010-05-05
Sweeeet. nVidia+Linux=woot.

---

### Post by -humanaut- on 2010-05-05
hmm... Seems I might have spoke to soon 3 reboots and it's failing already. This is pathetic.

---

### Post by speedwell68 on 2010-05-05
I have been having issues with this.  I get no splash screen at all.  I just get a split second of distorted grahpics at the top of the screen and the it goes blank.  TBH I am not that bothered as the splash screen is little more than eyecandy.

---

### Post by Queue29 on 2010-05-05
> **speedwell68 said:**
> I have been having issues with this.  I get no splash screen at all.  I just get a split second of distorted grahpics at the top of the screen and the it goes blank.  TBH I am not that bothered as the splash screen is little more than eyecandy.

It bothers me so much time/ resources is being wasted on this useless eyecandy, when there are so much more critical bugs to be squashed.

---

### Post by reyfer on 2010-05-05
> **Queue29 said:**
> It bothers me so much time/ resources is being wasted on this useless eyecandy, when there are so much more critical bugs to be squashed.

+1

What is SO important about this Plymouth that people want this fixed over other bugs?

---

### Post by Linuxforall on 2010-05-05
> **Queue29 said:**
> It bothers me so much time/ resources is being wasted on this useless eyecandy, when there are so much more critical bugs to be squashed.

Hear hear, nouveau and plymouth was a bad idea to start with, concentrate on real issues, not on eye candy, most with nvidia or ATI would go for proprietary drivers anyways, whats the point of all this nonsense really. Also Ubuntu is the fastest booting OS on earth period, why bother making few seconds worth of eye candy for the boot process, in my PC with nvidia drivers, I get a blinking cursor and then I am right on my desktop.

---

### Post by TheNerdAL on 2010-05-05
One question: Is the problem with the white underscore blinking on the black background on boot up fixed?

---

### Post by Water_Spirit on 2010-05-05
Like many users what I see when I'm booting is not important also like many users I only use Laptops and often only reboot when there is a kernel update or similar.

---

### Post by bikeboy on 2010-05-05
Let's us commit the fallacy of assuming resources devoted to fixing one problem automatically detract from the resources available to fixing another, *especially* in FOSS. If programmer/bug hunter A knows about project B and tries to fix it, how is them working on that going to slow down programmer X working on project Z?

It's a fallacy commonly seen when people talk about scientific research where they chastise, say, a physicist looking at black holes because it takes away from cancer research. Practically a *non-sequitur*, save for a little bit of funding allocation.

---

### Post by Queue29 on 2010-05-05
> **bikeboy said:**
> Let's us commit the fallacy of assuming resources devoted to fixing one problem automatically detract from the resources available to fixing another, *especially* in FOSS. If programmer/bug hunter A knows about project B and tries to fix it, how is them working on that going to slow down programmer X working on project Z?

It's a fallacy commonly seen when people talk about scientific research where they chastise, say, a physicist looking at black holes because it takes away from cancer research. Practically a *non-sequitur*, save for a little bit of funding allocation.

Your metaphor implies that plymouth is either interesting or useful, which it is not. It's like doing research to find a way to make red paint look more red. Instead of doing research on red paint, how about Canonical spend some money where it actually needs to be spent?

---

### Post by WinterRain on 2010-05-05
> **Linuxforall said:**
> Hear hear, nouveau and plymouth was a bad idea to start with, concentrate on real issues, not on eye candy

I know, they should just show a pretty picture that doesn't change, and forget about it. Or better yet, a black background with a simple progress bar at most. It's only a start up screen after all.

---

### Post by -humanaut- on 2010-05-06
> **Linuxforall said:**
> Hear hear, nouveau and plymouth was a bad idea to start with, concentrate on real issues, not on eye candy, most with nvidia or ATI would go for proprietary drivers anyways, whats the point of all this nonsense really. Also Ubuntu is the fastest booting OS on earth period, why bother making few seconds worth of eye candy for the boot process, in my PC with nvidia drivers, I get a blinking cursor and then I am right on my desktop.

I agree Nouveau and Plymouth being implemented in a new LTS was a terrible idea. X/Usplash worked fine. 

My PC (nvidia card) either shows a bloated logo, some distorted graphics or Plymouth just fails and drops me to a tty console. yes yes I know I have a freedom hating Nvidia card but until Nouveau works I want my Freedom hating drivers to work.

---

### Post by NightwishFan on 2010-05-06
Usplash has a lot of issues with many setups, and especially with kernel modesetting. (I believe) It really was not the way forward, but they should have had better fallbacks in 10.04 so at least we would get a splash and not just a text screen.

Before you say worry about critical bugs, note that plymouth is more than just a screen. It could soon make the boot experience great, especially considering open source drivers with KMS are maturing quickly.

Even among plymouth bugs the eye candy is less important.
[https://launchpad.net/ubuntu/+source/plymouth/+bugs](https://launchpad.net/ubuntu/+source/plymouth/+bugs)

---

