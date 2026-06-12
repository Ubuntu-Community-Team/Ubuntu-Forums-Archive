---
title: "Phenom II 965 or Core i7 860"
date: 2009-11-26
forum: The Cafe
---

### Post by piwacet on 2009-11-26
[Speaks like a pirate] Grrrr.... It's eating me up. There's no good 64 bit Linux benchmarks. Can't tell if the windows benchmarks matter... I've seen the phoronix stuff but their stuff is too vague (64-bit? 32-bit? 32 bit emulation under 64 bit? Weird or normal C-flags?). I live near a microcenter, so the total cost between AMD and Intel is not that different... I have a thing for the underdog, but if the i7 860 is really that much better, I'd go with that... 
 
I need to replace my current computer, and am thinking about both of these... if the AMD system was upgradeable to bulldozer or 6-core other chip in the future, that would be an advantage, but there are indeed no guarantees. Actually, the AMD motherboard I am considering is not even compatible with the C3 stepping of the current phenom IIs, unless you get the PCB revision 1.01g or higher (this board debuted in August 2009! - talk about not supporting future CPU's - the early revisions can't even handle a CPU from 3 months in the future!) 
 
What do you think?

---

### Post by toupeiro on 2009-11-26
> **piwacet said:**
> [Speaks like a pirate] Grrrr.... It's eating me up. There's no good 64 bit Linux benchmarks. Can't tell if the windows benchmarks matter... I've seen the phoronix stuff but their stuff is too vague (64-bit? 32-bit? 32 bit emulation under 64 bit? Weird or normal C-flags?). I live near a microcenter, so the total cost between AMD and Intel is not that different... I have a thing for the underdog, but if the i7 860 is really that much better, I'd go with that... 
 
I need to replace my current computer, and am thinking about both of these... if the AMD system was upgradeable to bulldozer or 6-core other chip in the future, that would be an advantage, but there are indeed no guarantees. Actually, the AMD motherboard I am considering is not even compatible with the C3 stepping of the current phenom IIs, unless you get the PCB revision 1.01g or higher (this board debuted in August 2009! - talk about not supporting future CPU's - the early revisions can't even handle a CPU from 3 months in the future!) 
 
What do you think?

I'm running the 940.  Some other things to keep in mind:

Intel = No northbridge at all.  Triple-channel RAMbus, much faster CPU/RAM I/O.  AMD's architecture will not surpass this until they evolve passed their current memory bus architecture.

Intel = Hyperthreaded quad-core (8 core virtual CPU).  Hyperthreading has come a long way from where it once was.  I've seen the benefits of this firsthand in the stuff I run.

If you are talking performance, and I mean really working the hell out of a system, AMD still can't touch an i7 chip.  However, for the price, the AMD is a damn good option.

---

### Post by piwacet on 2009-11-26
I think these 2 posts may be the best Linux 64 bit analyses available; done by a forum member of phoronix, Justapost, who says the results are reproducible, and who seems to have a handle on the turbo boost/c-states issue.  Justapost runs a 64 bit debian system, with identical graphics cards and memory(4GB) on each test system:

[http://www.phoronix.com/forums/showthread.php?t=18955&page=6](http://www.phoronix.com/forums/showthread.php?t=18955&page=6)

[http://www.abload.de/image.php?img=resultsyf3y.jpg](http://www.abload.de/image.php?img=resultsyf3y.jpg)

Justapost compares a stock i7 750 with a stock Phenom II 955, and also records results with c-states and/or turbo-boost disabled.  These are convincing numbers; turbo only enables the cpu to scale up to 2.8GHz, and with both c-states and turbo enabled, the cpu can scale up as high as turbo-boost allows.

In all, the core i7 750 wins at stock, and would only loose if both turbo and c-states are disabled.  The chart (second link) is very helpful.

In all, at stock, the chart indicates that on average the core i7 750 is 9% faster than the Phenom II 955.

---

### Post by Zoot7 on 2009-11-26
Up to you really, I've a Phenom II X4 955 and I'm pretty happy with it. My main reason for going AMD is that I think what Intel have done with the 3 sockets is an unmitigated disaster.

That said though, if I was in your position I'd probably go with the i5 as opposed the i7, as the i5 is better value for money.

---

### Post by rJ~ on 2009-11-26
On compatibility:
According to [http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=3673&p=2](http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=3673&p=2) at least some of the Bulldozer cores in 2011 will work on AM3* socket motherboards. I thought I read about a socket change, but that might have been for the server platform only.

*EDIT: I've seen other sites claim that Bulldozer will be using *AM3 R2*. No idea if that will be backwards compatible with AM3 like AM3 CPUs can be used in AM2+ boards.

Might want to wait for the new RD890 motherboards for a higher chance at Bulldozer compatibility. I read previously that they were supposed to be out by Q4 2009, but from the chart in the article it looks like it's been pushed to 2010. Also includes a new southbridge for hopefully better SATA performance.

From a short search on the C3 revision CPUs, it looks like AMD included some extra "magic" to lower the power use, hence needing updated PCB/BIOS on some motherboards.

If you're looking for an upgrade *right now*, I agree the i5 or i7 8xx series offer the best performance per price at the moment (Based on my memory of Windows benchmarks though).

I'm currently running using a PhenomII X4 940, had better performance/price for the only area I needed the high performance, gaming.

---

### Post by piwacet on 2009-11-26
Thank you all for allowing me to share my angst... I'll be looking at this...

---

### Post by cascade9 on 2009-11-26
> **toupeiro said:**
> I'm running the 940.  Some other things to keep in mind:
 
 Intel = No northbridge at all. Triple-channel RAMbus, much faster CPU/RAM I/O. AMD's architecture will not surpass this until they evolve passed their current memory bus architecture.
 
 Intel = Hyperthreaded quad-core (8 core virtual CPU). Hyperthreading has come a long way from where it once was. I've seen the benefits of this firsthand in the stuff I run.
 
 If you are talking performance, and I mean really working the hell out of a system, AMD still can't touch an i7 chip. However, for the price, the AMD is a damn good option.
 
 The i7 860 is LGA 1156. Dual channel, not triple. Its probably still faster than a Phenom II 965, but not as fast as benchmarking with triple channel LGA 1366 might suggest. 
 
 As for hyperthreading, it really helps in some areas, and doesnt help at all with others. IIRC. 
 
> **Zoot7 said:**
> Up to you really, I've a Phenom II X4 955 and I'm pretty happy with it. My main reason for going AMD is that I think what Intel have done with the 3 sockets is an unmitigated disaster.


+1. 

> **rJ~ said:**
> On compatibility:
According to [http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=3673&p=2](http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=3673&p=2) at least some of the Bulldozer cores in 2011 will work on AM3* socket motherboards. I thought I read about a socket change, but that might have been for the server platform only.

*EDIT: I've seen other sites claim that Bulldozer will be using *AM3 R2*. No idea if that will be backwards compatible with AM3 like AM3 CPUs can be used in AM2+ boards.

Might want to wait for the new RD890 motherboards for a higher chance at Bulldozer compatibility. I read previously that they were supposed to be out by Q4 2009, but from the chart in the article it looks like it's been pushed to 2010. Also includes a new southbridge for hopefully better SATA performance.

From a short search on the C3 revision CPUs, it looks like AMD included some extra "magic" to lower the power use, hence needing updated PCB/BIOS on some motherboards.

If you're looking for an upgrade *right now*, I agree the i5 or i7 8xx series offer the best performance per price at the moment (Based on my memory of Windows benchmarks though).

I'm currently running using a PhenomII X4 940, had better performance/price for the only area I needed the high performance, gaming.

Bulldozer is a whole generation, and 2011, away AFAIK,and will also be using a new (32nm) process. Who knows what will happen when the silicon gets out? Thuban (Phenom II X6, 6 cores, 45nm, 6MB L3, 512k x3 L2) I'm pretty certain will be on AM3 (possibly AM2+ as well).

---

### Post by cariboo on 2009-11-26
> **piwacet said:**
> [Speaks like a pirate] Grrrr.... It's eating me up. There's no good 64 bit Linux benchmarks. Can't tell if the windows benchmarks matter... I've seen the phoronix stuff but their stuff is too vague (64-bit? 32-bit? 32 bit emulation under 64 bit? Weird or normal C-flags?). I live near a microcenter, so the total cost between AMD and Intel is not that different... I have a thing for the underdog, but if the i7 860 is really that much better, I'd go with that... 
 
I need to replace my current computer, and am thinking about both of these... if the AMD system was upgradeable to bulldozer or 6-core other chip in the future, that would be an advantage, but there are indeed no guarantees. Actually, the AMD motherboard I am considering is not even compatible with the C3 stepping of the current phenom IIs, unless you get the PCB revision 1.01g or higher (this board debuted in August 2009! - talk about not supporting future CPU's - the early revisions can't even handle a CPU from 3 months in the future!) 
 
What do you think?

Fixed that for you:

> Grrrrrr.... It be eatin' me up, and dinna sparrrrre the whip! Therrre's no good 64 bit Linux benchmarks.  And swab the deck! Can't tell if th' windows benchmarrks matter... I've seen th' phoronix stuff but their stuff be too vague (64-bit? 32-bit? 32 bit emulation under 64 bit? Weird or norrrrrmal C-flags?), ye scurrvey dog.  I live near a microcenter, so th' total cost betwixt AMD and Intel be not that different.., to be sure.  I have a thin' fer th' underdog, but if th' i7 860 be really that much better, I'd go wi' that...

Install filters from the repositories and talk like:

> ken,  b1ff, censor, chef, cockney, eleet, fanboy, fudd, jethro, jibber&#8208;
       ish, jive,  kenny,  kraut,  ky00te,  nethack,  newspeak,  nyc,  pirate,
       rasterman, scottish, spammer, studly, uniencode, upside-down

---

### Post by BuffaloX on 2009-11-26
> **toupeiro said:**
> 
Intel = Triple-channel RAMbus.

I'll avoid RAMbus as long as it is at all possible.
They are no better than SCO IMO.

---

### Post by cascade9 on 2009-11-26
I think toupeiro meant 'triple channel ram bus', not Rambus DRAM. The Intel i875 (dual DDR400) chipset pretty much killed RD-RAM. 

They have tried again, with XDR-RAM, and XDR2 but PC makers left it alone. Thats what happens when you go around sueing as many protential partners as RDRAM did. Made even worse by the fact that Rambus is totally fabless, they have to have partners to build anything.  ** **

---

### Post by BuffaloX on 2009-11-26
Thanks, that also makes more sense, I guess I just had a knee jerk reaction to the word RAMbus.

Intel might try again, they did buy a lot of stock in Rambus, and tried to make it a standard only making chipsets for Rambus for a while, luckily they failed.

Personally I prefer AMD CPUs, because Intel is a near monopoly, and I don't support monopolies.

AMD is a little behind in the performance race, but in a couple of months you wont have top performance anyway, no matter what you buy now.
Look at performance/cost unless you have more money than you need, and also consider if you want an Intel monopoly.

The only reason Intel offer such a good processor ATM, is because they are competing with AMD.

---

### Post by cascade9 on 2009-11-27
Its always possible that RAMbus will come back into computers, but I really, really doubt it. the i820/i840 chipsets (1st from intel with RDRAM) were, frankly, awful. The i850 was pretty good for the early/mid p4s but the cost of RDRAM,a nd the premuim intel charged for the i850 chipsets drove almost everybody away. 

AMD is behind on performance, but thats hardly suprising. Intel has roughly 75-80% of the (x86) market share. AMD has aprox 15%. Thats a lot more money for R+D for Intel. Intel also gets the newer fab plants before AMD, in part from market share, in part from previous agreements. 

Not knocking AMD at all, they are a good company, have some great products, I actually prefer AMD myself.  But that mid1999 to 2006 period when AMD could claim to have faster, or at least as fast CPUs as Intel was just as much from Intel dropping the ball (RDRAM, P4 CPU) as anything AMD did.  

I doubt that we will ever see AMD challenge Intel like we saw in that period. At least AMD did manage to really get under intels skin (1st 1Ghz CPU, AMD_64 in particular). But in some ways you have a point....if, say, AMD was still stuck on dual-core CPUs, I dont know if the i7s and i5s would have come out yet. Intel may very well have kept pushing the Core 2 Duos for a lot longer. 

BTW, if AMD do ever seriously challenge Intel again, watch out Intel buyers. When Intel feels threatened is when they release crappy CPUs (e.g. P3 600 'katmai', P3 1Ghz, P3 1.13, P4)

---

### Post by BuffaloX on 2009-11-27
I totally agree.
It was easy to be an AMD supporter for many years, since they had the superior products and reasonable prices. Weird how Intel was able to keep their market share so high especially with their lousy P4.

I think AMD still offer great CPUs at very reasonable prices. Especially if you go slightly below the top performers.

---

### Post by Vaphell on 2009-11-27
> Weird how Intel was able to keep their market share so high especially with their lousy P4.

this is called 'abusing weight in the market'. AMD64 simply owned lame P4's. AMD should have increased their market share substantially which means more profit and more money for r&d. Unfortunately intel blackmailed comp shops not to buy AMD chips or else they will lose bonuses (as shown by recent investigations in EU) - nobody dared to test intel's patience and most shops caved in. AMD was literally unable to give CPUs away for free.
Intel with these dirty tricks bought necessary time, poured obscene amounts of cash on the problem and some time later came up with C2D. Opportunity window of AMD got sealed.

When a company blows so much money on R&D and can't sell its superior product, don't be surprised it can't compete later, it's stuck with the bills deep in the red and has to think more about survival now.

---

### Post by LowSky on 2009-11-27
lets not make this why Intel controls the market, and what this person should buy

Personally go AMD, its cheaper for perfomance per dollar. You can buy dual channel ram instead of triple channel. 

I have a Phenom II x2 550 unlocked to 4 cores and over-clocked to 3.5Mhz That chip was $100 and is now as fast as a Phenom II x4 955, and I know it will over-clock higher.

I dont know any Intel chips that do that.

---

### Post by toupeiro on 2009-11-27
> **BuffaloX said:**
> I'll avoid RAMbus as long as it is at all possible.
They are no better than SCO IMO.

LOL good catch.  I forgot all about RAMBus memory.  No, this is indeed DDR-3 RAM, but my 940 uses a triple channel memory bus, bad use of terminology on my part. :P

---

### Post by piwacet on 2009-11-27
Well, I went with the AMD setup.  Thanks all for the time and input, was very helpful.

(And feel free to continue some of the various threads of conversation if you want...)

Thanks!

---

### Post by cascade9 on 2009-11-27
@ touperio- not bad, maybe just 'miscapitalised'. 

@ piwacet- hope you enjoy your new system! :) 

> **Vaphell said:**
> this is called 'abusing weight in the market'. AMD64 simply owned lame P4's. AMD should have increased their market share substantially which means more profit and more money for r&d. Unfortunately intel blackmailed comp shops not to buy AMD chips or else they will lose bonuses (as shown by recent investigations in EU) - nobody dared to test intel's patience and most shops caved in. AMD was literally unable to give CPUs away for free.
Intel with these dirty tricks bought necessary time, poured obscene amounts of cash on the problem and some time later came up with C2D. Opportunity window of AMD got sealed.

When a company blows so much money on R&D and can't sell its superior product, don't be surprised it can't compete later, it's stuck with the bills deep in the red and has to think more about survival now.

AMD 64 was pretty late. The Early P4s were up against athlon and athlon XP. The early P4s (400FSB 256k model) and were even more owned by the XPs than later P4s were against the AMD64s. I dont think it even started there, the AMD K6/3 was Very Fast...not than many people, even at the time, had any idea what a K6/3 was. 

I dont think that Intel 'blackmailed' shops. I would like to see decent links if people have said they did though. :) 

A lot of AMDs problems were that they had virtually no support from the teir 1 manus (dell, acer, HP, etc..and there probably was blackmail involved in that) and thats where the majority of sales happened. Another issue was that people who bought AMD tended to be more money concious, and when they 'built down to a price' they tended to get cheap motherboards, PSUs, RAM, etc. A recipie for something to go wrong, and when it did, they blamed AMD, not cheap parts. Also, the P4s tended to do better at framerates, which tended to be one of the major benchmarks people looked at. For desktop use an Athlon/Athlon XP was noticably faster, but it didnt look that way unless you checked the right benchmarking. 

Also, AMD has never had the amount of fab plants that Intel has. I remember when I got my Athlon 1200C, there was shortages of the middle range CPUs. (i.e. the CPUs people actually bought). Top end and bottom end AMD CPUs were less of a problem.   

AMD seems to be competing just fine with Intel now. Yes, they have had money issues but from what I've seen AMD has picked up quite a few % points vs Intel in the last few months. 

You dont need the fastest CPU to compete. Some people think you do, mind you. Price/performance isvery important, and AMD has always done well on that basis.

---

### Post by Grifulkin on 2009-11-27
AMD ftw.

---

