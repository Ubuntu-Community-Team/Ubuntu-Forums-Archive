---
title: "SLI or CrossFire impact on HD Video for HTPC"
date: 2009-12-25
forum: The Cafe
---

### Post by crazyness003 on 2009-12-25
I'm in the process of shopping for components to build an HTPC system for a friend. During my search, I was wondering if I should spend the extra $ for a CrossFire or SLI Mobo, since the rig will be primarily used as an HTPC for HD video. I know multi-GPU systems increase framerate for rendering games, but how much of an increase will it be for HD video (from a TV tuner, Blu-Ray or HDD)?

I know there are other places to ask this, but I honestly don't know where. So, I come to you, fellow Ubuntu Users, for guidance. Also, if you could tell me a batter place to ask, that too would be appreciated.

I was also thinking of installing MythBuntu on it, but I'll have to talk it out with him (if he's comfortable running GNU/Linux or if he should dish out for Win7).

Again, thanks.

---

### Post by crazyness003 on 2009-12-26
bump

---

### Post by insane_alien on 2009-12-26
seeing as my integrated intel graphics can play 1080p flawlessly i'm going to say SLI and crossfire have precicely zero effect as the single car will be more than capable of handling it with plenty to spare.

all it will do is suck up power.

---

### Post by McButt on 2009-12-26
Adding a second card wouldn't make a difference regarding video playback. The only reason to even consider multi-gpu setups is if you're a serious gamer who wants to play everything at super high resolutions with maxed out settings. For a htpc you really don't need that much raw graphics power, you only need to make sure the card can decode video.
Assuming you'll be using linux I'd advise you to get an nvidia card since the recent ones have vdpau support.
[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)
If you look at that wiki page you'll see that you really don't need to spend alot of money on a graphics card for a htpc. In fact using an 'overpowered' card will only consume more power and generate more heat wich will make it harder to keep the noise levels of your htpc acceptable.

---

### Post by mr clark25 on 2009-12-26
i would make shure your motherboard has enough paths in the southbridge for two video cards, a tuner, and whatever else you may want.
 i am looking into buying an asus p6t for an i7 setup. the southbridge has only 36 paths, and i wanted two video cards. the video cards were x16 pci-e video cards. (the number after the x is how many paths it uses) so, that would fill up 32 paths. that only leaves 4 for me to use for other things. i could use more (paths), but then the video cards would only get x8 each (8 paths), killing their performance.

so, you should make sure you have enough paths on your motherboard to have dual video cards and everything else you want.

i think that having them in dual does increase performance by a lot. (or at least that is what i have read)

---

### Post by insane_alien on 2009-12-26
> **mr clark25 said:**
> 
i think that having them in dual does increase performance by a lot. (or at least that is what i have read)

yes, for games, not video playback. 

having SLI for video playback is like attaching some space shuttle engines to a car in order to drive at 20mph.

lots of power but its just not being used for anything.

---

### Post by Exodist on 2009-12-26
> **crazyness003 said:**
> I'm in the process of shopping for components to build an HTPC system for a friend. During my search, I was wondering if I should spend the extra $ for a CrossFire or SLI Mobo, since the rig will be primarily used as an HTPC for HD video. I know multi-GPU systems increase framerate for rendering games, but how much of an increase will it be for HD video (from a TV tuner, Blu-Ray or HDD)?

I know there are other places to ask this, but I honestly don't know where. So, I come to you, fellow Ubuntu Users, for guidance. Also, if you could tell me a batter place to ask, that too would be appreciated.

I was also thinking of installing MythBuntu on it, but I'll have to talk it out with him (if he's comfortable running GNU/Linux or if he should dish out for Win7).

Again, thanks.

Multi GPUs will not help with video playback. That goes through the video cards RAMDAC, which most all these days are 400mhz.

---

### Post by 3rdalbum on 2009-12-26
A multi-card setup does not help video decoding performance.

---

### Post by crazyness003 on 2009-12-26
Thanks all. I was pulling towards the "I don't really need it" side; but I just wanted to make sure. Not only is buying another GFX card unresourcefull, but the mobos that are needed to support multi-GPU systems also cost more money.

plus this gives me an idea on how to present the plan to exclude multi-GPUs to my friend.

Again, thank you all for your time.

---

### Post by McButt on 2009-12-26
Just remembered this article showing how little hardware you really need for HD playback on linux. Show it to your friend if he needs some more convincing :)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_vdpau_gpu&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_vdpau_gpu&num=1)

---

### Post by crazyness003 on 2009-12-27
I dont know, he's kinda afraid to jump into the linux waters. I told him that Ubuntu has the largest community for help (if needed). I think he just wants to be more comfortable using Windows <*whatever*>. Unfortunately, I dont have a lot to time to dedicate to helping him if a problem does arise (with my luck, there's always a problem).

Anyway, Yeah, I'll show this article to him, but he wont understand. Even if I spoon feed him.

Thats the advantage and downfall of choice.

Anyway, thanks for the article, I'm gonna use that for my own HTPC (which I plan on building soon).

---

### Post by Frak on 2009-12-27
Multiple cards != better decoding.

---

### Post by crazyness003 on 2009-12-27
> **Frak said:**
> Multiple cards != better decoding.
Thanks Frak, but you're only A DAY TOO LATE. I'm just kidding.

I realized this was fact, I just wanted to confirm. Plus now I have an arsenal of information to give to my buddy.

Oh, and nice avatar ;)

---

### Post by Frak on 2009-12-27
> **crazyness003 said:**
> Thanks Frak, but you're only A DAY TOO LATE. I'm just kidding.

I realized this was fact, I just wanted to confirm. Plus now I have an arsenal of information to give to my buddy.

Oh, and nice avatar ;)
>:O|o>

It's a TF2 spy with a camera beard :D

---

### Post by crazyness003 on 2009-12-27
> **Frak said:**
> >:O|o>

It's a TF2 spy with a camera beard :D
Nice! But, why is he so angry?

---

### Post by Frak on 2009-12-27
> **crazyness003 said:**
> Nice! But, why is he so angry?
The spy is always angry.

> Originally said by **The Spy**
*Come stand on the point you imbecile!*

---

