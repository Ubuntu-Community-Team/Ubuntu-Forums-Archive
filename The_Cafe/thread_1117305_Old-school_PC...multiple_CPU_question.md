---
title: "Old-school PC...multiple CPU question"
date: 2009-04-05
forum: The Cafe
---

### Post by dbsoundman on 2009-04-05
I managed to get an old Dell Workstation 420 for free recently, and I decided to use it as a kind of living room media station. Right now it only has 1 Pentium 3 Coppermine CPU in it, 733MHz. I'm pretty sure that the mobo in these things allowed for multiple CPUs though, so I'm thinking of adding another CPU, since I can snag them for like $4 apiece on ebay these days. This means I have a few questions...

First, do I have to have 2 CPUs that run at the same speed; i.e. can I just put in a 1GHz P3 in there with the 733, or do I need two 733s or two 1Gs?

Second, this is going to sound incredibly idiotic, but can I run windows 95 on this system with 2 CPUs? I installed 95 to run some old games and just as kind of a fun nostalgia experience. It seems that most virtual machines don't play nicely with 95, so it seemed like the easiest way to go about it was to actually make a real install. I'm just not sure how 95 handles multiple CPUs, or if it does so at all.

This is part of my never-ending saga of making old, obsolete hardware work for my applications. Hopefully this isn't too "tech support" for the café here, I just trust the knowledge base of the ubuntu forums a bit more than other forums, so I wanted to ask you all here. Thanks!

-Dan

---

### Post by Mehall on 2009-04-05
a PIII is NOT obsolete hardware!!!

granted, with 256MB RAM it struggled, but I have a 1GHz PIII Coppermine that had XP for ages and did fine (It's on Arch now ;)

And no clue about the multiple CPU thing, but if you can see a socket for a second CPU, go for it, though i think they have to be matched, and 95 probably doesn't have multi-cpu support, btu I believe 98SE does.

---

### Post by dbsoundman on 2009-04-05
Thanks, I do have a Windows 98SE disk so I could do that, but I was kind of hoping to use 95 just for the fun of using the old Microsoft Plus! themes I found. I even downloaded old versions of Netscape Navigator to run on there ;). But, at the same time, I'm pretty sure there are Windows 98SE drivers for the onboard soundcard, whereas there are none for 95, so in order to get sound for 95 I had to go buy a really cheap soundcard and use that instead. I suppose I should also see how many of these games actually work in Wine; the main one I wanted to play was "The Neverhood", and I recently found out that works fine in wine (haven't played it a lot on there though). I guess I have to experiment some...

-Dan

---

### Post by Mehall on 2009-04-05
Most older stuff works Fine in WINE

and if it's DOS stuff you have as well as Win stuff, don't forget about DosBOX or FreeDOS (I advise Dosbox first)

---

### Post by dbsoundman on 2009-04-05
I just opened up the PC, and realized that what I need are Pentium III Slot 1 processors with heatsinks. It appears that the 1GHz versions are harder to find, but the 733s are easy to find, so I'll probably go with another 733 for a total of 1466MHz, not bad. I'm also thinking of getting more RIMM memory (I have 512 right now). Any tricks to RIMM or can I just get any brand? I want to get another pair of 256 so I can get up to 1GB of RAM. I'm guessing RIMM is like DIMM in that it's brand-independent. RIMM, as well, seems to be expensive in 256 form but cheap in 128...go figure.

Thanks,
Dan

---

### Post by Mehall on 2009-04-05
> **dbsoundman said:**
> I just opened up the PC...and I'm a little confused. I definitely know there's 2 CPU slots, and I know from the BIOS that the CPU in there right now is a 733 MHz Pentium III coppermine, but there's a couple puzzling elements. First, in the second CPU slot, there's some sort of other card inserted. I don't think it's a CPU, but it's just some sort of board that fits in the slot. Second, the CPU that is in the first slot is in some sort of big, black card of some sort, and has a HUGE aluminum heatsink on it. So, assuming I do get another CPU, I'm guessing I will need to find the card adapter that fits it into that vertical slot, and another heatsink, correct? What I'm seeing on ebay is lots of processors, but no assemblies. Any ideas on how to find these things?

Thanks,
Dan

I'm afraid I've only ever messed about with a few multi-CPU MoBo's in my time, all of which had full CPU's and the heatsinks, etc. in them already, as they were ex-workhorse servers. (And too slow for them to be worth me risking nicking ;)

---

### Post by dbsoundman on 2009-04-05
Thanks, I just edited my post as you were replying, I did a little bit of research and pieced together the puzzle. I need the Pentium processors in the Slot 1 form, which I was able to find on the bay. Now I just need to suss out the memory type I need.

-Dan

---

### Post by Mehall on 2009-04-05
Never used RIMM's I'm afraid... But happy hunting!

I look forward to hear how this ends up. [=

---

### Post by dbsoundman on 2009-04-05
Thanks! I'm bidding on a second CPU right now, and assuming I get an answer soon about the RIMM I'll pick that up as well. I've already added a better CD-ROM drive (upgraded to a DVD-ROM with write support). I also did some reading, and Windows 95 and 98 do not support multiple CPUs, but they will run on a multi system; they just ignore the second CPU. Windows 95 is pretty friggin' fast on a 733MHz with 512MB RAM as it is, so I doubt I'll need the second processor on that one anyway :) . The main reason for this upgrade is I found that the machine is a bit slow when running internet video in ubuntu; lots of frame skipping, especially in fullscreen mode. Since I may very well use this more for watching movies on the TV than anything else, I figure it's worth ~$40 to make it comparable to a decent "modern" machine.

-Dan

---

### Post by Mehall on 2009-04-05
> **dbsoundman said:**
> Thanks! I'm bidding on a second CPU right now, and assuming I get an answer soon about the RIMM I'll pick that up as well. I've already added a better CD-ROM drive (upgraded to a DVD-ROM with write support). I also did some reading, and Windows 95 and 98 do not support multiple CPUs, but they will run on a multi system; they just ignore the second CPU. Windows 95 is pretty friggin' fast on a 733MHz with 512MB RAM as it is, so I doubt I'll need the second processor on that one anyway :) . The main reason for this upgrade is I found that the machine is a bit slow when running internet video in ubuntu; lots of frame skipping, especially in fullscreen mode. Since I may very well use this more for watching movies on the TV than anything else, I figure it's worth ~$40 to make it comparable to a decent "modern" machine.

-Dan

You're gonna hate me, but not long ago I got a complete System for free.

AMD XP 2000+ (so equivalent to a 2.0 or 2.1 GHz P4) with 256MB of RAM (upgradeable to 2GB max, and I'm working on that, for free ;)

I just need to get a Video card and it will play The Orange Box ;)

---

### Post by dbsoundman on 2009-04-05
Nice! I used to have an AMD XP machine...it was a lower speed, I think it was maybe around 1MHz with 1GB of RAM. Too slow for me and my multitasking, VMs, etc. This machine I got was completely free, the only thing it lacked was a hard drive, and I happened to have a spare 80GB IDE drive I wasn't using, so I dropped that in and presto. Oh, I did have to buy a monitor for like $5 at the thrift store, and a $1 keyboard. It's a surprisingly decent machine, I'm just hoping to make it even more decent. I'm setting it up as a sort of client and server for videos, so that way I can access any videos on my desktop machine in my room on that computer and watch them, and I or my roommate can also upload movies to this computer to watch on there as well. I've got a regular CRT TV, so I bought some cheapo VGA to S-Video adapter box to use with it. The resolution isn't fantastic, but when you're watching movies it's not bad at all really (just hard to read text at 1024x768 resolution).

-Dan

---

### Post by spcwingo on 2009-04-05
It is recommended to install two of the same processors.  Instead of digging around for slot 1 1Ghz processors, just invest in 2 slockets (adapters that allow you to use socket 370 processors in slot 1 boards).  After that I believe you will be golden.

---

### Post by dbsoundman on 2009-04-05
Thanks for the tip, I was wondering if those things had a name! I'm already bidding on a slot 1 733 with heatsink on ebay right now, but if that falls though I may consider the slocket route, although as it is I wouldn't gain much by upgrading to 2 1GHz processors. I read that if you have a dual processor setup, to find the actual speed you should multiply a single processor's speed by 1.7. So that means with two 733s I'd get around 1.2GHz, and with 2 1Gs I'd get about 1.7GHz. I'm pretty sure for video playback I don't need a whole lot of firepower, and I think adding more memory will also help with that issue. As it is, regular DVD video is fine, it's just internet browsing and streaming video that doesn't play so nicely.

-Dan

---

### Post by wolfen69 on 2009-04-05
> **dbsoundman said:**
> so I'll probably go with another 733 for a total of 1466MHz, not bad.

two 733mhz cpu's do not equal 1466mhz worth of cpu. it does not work that way. apps need to be written for 2 processors to take advantage of it. your cpu speed overall will still be 733mhz. old programs will definitely not be written for dual cpu's. you will be wasting your money if you intend to run win98. 98 will run great on 1 cpu alone. memory would be the most important thing. you won't see 1 bit of difference between running 1 or 2 cpu's. especially with win98. don't believe me? go ahead and waste your money.

i have a quad core processor running at around 3.0ghz each, but that does not mean i now have 12ghz processing power. get my drift?

---

### Post by dbsoundman on 2009-04-05
I realized later that it wouldn't actually add up algebraically, but I was under the impression that they would still work together as the dual core processors do. Am I right in thinking this?

I know Windows 98 can't take advantage of both processors, but it doesn't need it anyway. Mainly I'm doing this for my Ubuntu install on this computer, so that it runs more smoothly with digital video in general. I'm definitely maxing out the memory too (a whole 1GB, woo hoo!).

-Dan

---

### Post by wolfen69 on 2009-04-05
> **dbsoundman said:**
> I was under the impression that they would still work together as the dual core processors do. Am I right in thinking this?


no, you are not. it may help your ubuntu install, but windows 98 will not see any advantage.

---

### Post by Mehall on 2009-04-06
> **wolfen69 said:**
> no, you are not. it may help your ubuntu install, but windows 98 will not see any advantage.

He knows that (win98 doesn't do well w/ multi-cores, not just multi CPU's) but he meant inside Ubuntu/other linux, would the two CPU's work roughly in a way equivalent to running a dual-core machine,

---

