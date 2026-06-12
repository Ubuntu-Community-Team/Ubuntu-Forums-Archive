---
title: "What's most important for the speed of DVD ripping?"
date: 2011-06-26
forum: The Cafe
---

### Post by Dustin2128 on 2011-06-26
I finally, finally have enough money for some major upgrading and I'm wondering- what most affects the speed of ripping dvds? Is it clock speed, number of processor cores, cache size, or what? It annoys me that my current, fairly recent system can rip dvds barley faster than it takes to watch them. I'm going for an AM3 processor, so I'd like to know what matters more- having that quad core athlon or having a dual core phenom with L3 cache?

---

### Post by christopher.wortman on 2011-06-26
Even with a Core i7 encoding DVDs takes a fair amount of time. What you need to realize is that you don't have permission to rip DVDs even if you own a physical copy of it. Asking such questions is squarely prohibited.... Ok I couldn't keep going with a straight face XD but for video go Intel lol. The new sandybridge is amazing for video editing and stuff.

---

### Post by Dustin2128 on 2011-06-26
Curses, I have not the money for sandy bridge processors. Is it really that much better? I might be able to afford one of the lower end i5 SBs.

---

### Post by christopher.wortman on 2011-06-26
Even the core i3 sandybridge makes that much difference. AMD is coming out with a new core, but not for a while. Intel has the market right now for most anything you want to accomplish. HOWEVER AMD is better at handling your wallet. You will see a definite performance gain. AMD is more consistent and cleaner processing, but Intel once again out of nowhere pulls raw power then makes up for it with software coding things in BIOS. They have done it this way for years and have become quite good at it. For pure power go AMD, for everything desktop related go Intel.

---

### Post by Dustin2128 on 2011-06-26
> **christopher.wortman said:**
> Even the core i3 sandybridge makes that much difference. AMD is coming out with a new core, but not for a while. Intel has the market right now for most anything you want to accomplish. HOWEVER AMD is better at handling your wallet. You will see a definite performance gain. AMD is more consistent and cleaner processing, but Intel once again out of nowhere pulls raw power then makes up for it with software coding things in BIOS. They have done it this way for years and have become quite good at it. For pure power go AMD, for everything desktop related go Intel.
Here's the thing, my budget for CPU is 130$ maximum, and the only respectable sandy bridge cpu in that range is an i3 model with half the L3 cache, 800MHz lower clock and 3 fewer physical cores than the Phenom II I'm looking at. Video encoding is something I do rarely, but quite often, when it does come up, it's a time sensitive thing (ripping dvds to watch on a portable device with no optical drive for a long car trip). I highly doubt such a weak chip could out perform a high end phenom II, revolutionary architecture or no.

---

### Post by doas777 on 2011-06-26
System Bus and IO Bus as well as player speed are some of the biggest bottlenecks, though CPU does come into play. I would go with raw ghz rather than cores though, since I don;t think multithreading the task in this case would be possible.

look for a 1666mhz FSB for your mobo, ram and cpu. if you can try to find sata3 io ports and drives. make sure you have plenty of free ram so you don;t need to buffer anything to disk.

thats about the best I can recommend.

---

### Post by Dustin2128 on 2011-06-26
> **doas777 said:**
> System Bus and IO Bus as well as player speed are some of the biggest bottlenecks, though CPU does come into play. I would go with raw ghz rather than cores though, since I don;t think multithreading the task in this case would be possible.

look for a 1666mhz FSB for your mobo, ram and cpu. if you can try to find sata3 io ports and drives. make sure you have plenty of free ram so you don;t need to buffer anything to disk.

thats about the best I can recommend.
I'll look into a 1666MHz FSB, no to SATA3 drives, I'm just using the ones in my old computer to save cash. I'm going for at least 8GB of DDR3 1333 RAM, so memory will be a non issue.
EDIT:What exactly is hypertransport? For FSB choices, I've got 3 speeds, 1000, 2200, and 2600MHz, the majority being 2600.
Also, off topic and out of curiosity, is it possible to run my 2 head GPU and onboard video at the same time for tri monitor support?

---

### Post by alphacrucis2 on 2011-06-26
> **Dustin2128 said:**
> I'll look into a 1666MHz FSB, no to SATA3 drives, I'm just using the ones in my old computer to save cash. I'm going for at least 8GB of DDR3 1333 RAM, so memory will be a non issue.
EDIT:What exactly is hypertransport? For FSB choices, I've got 3 speeds, 1000, 2200, and 2600MHz, the majority being 2600.

No matter what you do, you are going to be limited by how fast the DVD player can read the DVD's. IMO that is going to be the main bottleneck on any modern machine. The DVD has to be physically spun faster to read it faster.

---

### Post by doas777 on 2011-06-26
> **Dustin2128 said:**
> I'll look into a 1666MHz FSB, no to SATA3 drives, I'm just using the ones in my old computer to save cash. I'm going for at least 8GB of DDR3 1333 RAM, so memory will be a non issue.
EDIT:What exactly is hypertransport? For FSB choices, I've got 3 speeds, 1000, 2200, and 2600MHz, the majority being 2600.
Also, off topic and out of curiosity, is it possible to run my 2 head GPU and onboard video at the same time for tri monitor support?

Hypertransport is a technology on the system bus that acts much like front side bus on intel.
Intel system buses use "Dual Channel Memory" so that two bus tasks can access memory at once, but when they report the speed in documentation, they state the speed of each bus (eg 533, 800, 1066, 1333, 1666) but AMD adds both channels bandwidth together in their documentation (533 -> 1000, 800 -> 1600, 1066 -> 2200, 1333 -> 2600). you can compare apples to apples if you divide amd roughly by 2.

---

### Post by doas777 on 2011-06-26
> **alphacrucis2 said:**
> No matter what you do, you are going to be limited by how fast the DVD player can read the DVD's. IMO that is going to be the main bottleneck on any modern machine. The DVD has to be physically spun faster to read it faster.
true, a x24 drive will read about 32MB/s so most hdds should be able to double that on decent hardware. at the same time, my systems never seem to be able to reach that speed, though faster ram feels like it has made a difference.

---

### Post by Dustin2128 on 2011-06-26
> **doas777 said:**
> Hypertransport is a technology on the system bus that acts much like front side bus on intel.
Intel system buses use "Dual Channel Memory" so that two bus tasks can access memory at once, but when they report the speed in documentation, they state the speed of each bus (eg 533, 800, 1066, 1333, 1666) but AMD adds both channels bandwidth together in their documentation (533 -> 1000, 800 -> 1600, 1066 -> 2200, 1333 -> 2600). you can compare apples to apples if you divide amd roughly by 2.
Looks like I'm out of luck on that front then... I'm assuming though, that ripping will be... acceptably fast on a 3.7GHz (planned 400MHz oc), so I guess I'll just take a weekend and rip my whole collection to some terabyte drives when I get the money for them. Thanks for the help everyone.

---

### Post by handy on 2011-06-26
I'd say (if you are using HandBrake or something else that is capable) the number of cores that you have available for the job.

---

### Post by Dustin2128 on 2011-06-26
> **handy said:**
> I'd say (if you are using HandBrake or something else that is capable) the number of cores that you have available for the job.
I am using handbrake actually, and I've decided to cut back on the case a bit for a quad core phenom II black edition- 6MB L3 cache as well, and a 3.2GHz clock that I'm upping to 3.7 or 8. If I can find a decent cooler, I might even go for 4.

---

### Post by NightwishFan on 2011-06-27
I get 40-60fps on rips using my Intel t4400 (2.2ghz). A quad core machine using handbrake should be very fast.

---

### Post by nec207 on 2011-06-27
If you into ripping DVD and video editing get the most expensive video card you can get  or you will spend days.
 
It took me 30 minutes just to do video editing on a 10 minute clip cut to a 2 minutes of good video.
 
Now I'm thinking I need a bettter computer.
 
The intel i5 is not that much faster than the intel core 2 duo. It is not going be 2 or 3 times faster.

---

### Post by cariboo on 2011-06-27
I fail to see why dvd rip speed should be a concern, it's not like you have to sit there and watch the process. Linux is a multitasking OS, you can do something else while the rip is in progress.

---

### Post by handy on 2011-06-27
> **NightwishFan said:**
> I get 40-60fps on rips using my Intel t4400 (2.2ghz). A quad core machine using handbrake should be very fast.

I was looking on the Apple site yesterday & noticed that they currently sell a Mac Pro with 12 cores!

If that only made the processing power 6 times faster than the average time of my old C2duo, I'd be ripping a DVD in 15 minutes.

I suspect that the 12 core could be faster than that.

That really is a lot of horsepower there.  :shock:

---

### Post by handy on 2011-06-27
> **cariboo907 said:**
> I fail to see why dvd rip speed should be a concern, it's not like you have to sit there and watch the process. Linux is a multitasking OS, you can do something else while the rip is in progress.

It would certainly be of benefit if you have the tedious job of ripping ~600 DVDs onto your HDD. It took me months with 2 machines running everyday.

---

### Post by mips on 2011-06-27
> **Dustin2128 said:**
> Curses, I have not the money for sandy bridge processors. Is it really that much better? I might be able to afford one of the lower end i5 SBs.

The i5 2500K SB is a good performer. Get a P (I think?) series MB to go with it and then you can also overclock it a lot.
For encoding stuff more cores is better.

I would not buy AMD right now (I'm a AMD fan btw) as the Intels performs so much better.

If you want some good budget i5 build suggestions PM me and I will point you to a forum where this topic comes up almost every single day.

Always rip to HDD before encoding, encoding straight from DVD is slow.
So also get the fastest optical drive and HDD (7200rpm 32MB cache)

---

### Post by nec207 on 2011-06-27
Get a intel i7 4 core or AMD 6 core .Stay away from i3 2 core or i5 2 core it not going be 2 or 3 times faster than a intel core 2.

---

### Post by halibaitor on 2011-06-27
I don't think having a multi-core processor is necessarily the answer.  I typically rip a 2 hour DVD in 12 minutes or so with an old P4 2GHz machine.  I think your perceived slowness is more apt to be caused by the software you are using.  

I was also told (can't prove it however) that if a particular program isn't written for a multi-core processor, that you get no speed increase from using one.

As always, YMMV.  ;)

---

### Post by nec207 on 2011-06-27
> **halibaitor said:**
> I don't think having a multi-core processor is necessarily the answer. I typically rip a 2 hour DVD in 12 minutes or so with an old P4 2GHz machine. I think your perceived slowness is more apt to be caused by the software you are using. 
 
I was also told (can't prove it however) that if a particular program isn't written for a multi-core processor, that you get no speed increase from using one.
 
As always, YMMV. ;)
 
That is right but good code OS should make use of the cores no matter if the bad old code software .
 
Also you need a good video card. It not only the CPU but good video card with a good GPU.

---

### Post by halibaitor on 2011-06-27
OK, but the video card will have more to do with streaming video, high speed games with lots of rendering going on, etc.  The original question had to do with ripping, and the video card should have nothing to do with that...  (not that I have anything against a good video card)

---

### Post by doas777 on 2011-06-27
I am thinking that for simply ripping, cores makes no difference. IO off a single disk will only server one thread at a time. most dvd rippers read a raw stream off the media, and that is best done synchronously. 

[handbrake]("https://trac.handbrake.fr/wiki/SupportFAQ#whatisit")'s Transcoding routine is multi-threaded and can make use of multiple cores however. if transcoding is part of what you want to do Dustin, then cores matter much.

> **halibaitor said:**
> 
I was also told (can't prove it however) that if a particular program  isn't written for a multi-core processor, that you get no speed increase  from using one.


This is true. a multi-threaded application or an app that runs multiple  processes can make use of multiple cores, running a thread per core.

---

### Post by Dustin2128 on 2011-06-27
> **nec207 said:**
> That is right but good code OS should make use of the cores no matter if the bad old code software .
 
Also you need a good video card. It not only the CPU but good video card with a good GPU.
Video card's no issue, 9600 GT 512Mb. I may just wait for bulldozer but I'm pretty impatient with AMD since it was supposed to have come out years ago ;).

---

### Post by nec207 on 2011-06-28
> **halibaitor said:**
> OK, but the video card will have more to do with streaming video, high speed games with lots of rendering going on, etc. The original question had to do with ripping, and the video card should have nothing to do with that... (not that I have anything against a good video card)
 
A video card will help with video editing .

---

