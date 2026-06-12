---
title: "GNU/Linux PC Gaming on AMD PCs"
date: 2016-02-07
forum: The Cafe
---

### Post by Welly Wu on 2016-02-07
To the best of my memory (which is quite excellent), I never bought a desktop or notebook PC with AMD CPUs and GPUs and RAM along with SSDs or HDDs (which they don't make) in several long years. I am curious about AMD technologies like CPU, GPU, RAM, and possibly SSDs to gather some research to buy a ZaReason desktop PC that has as much AMD technology as possible sometime in the future. Right now, ZaReason sells their Limbo and Fortis Extreme desktop PCs, but I am not interested in the older AMD CPUs. I am more interested in the upcoming AMD Zen CPU and AMD Polaris 16 nm FinFET GPUs coming later this year. While I could teach myself to build my own AMD desktop PC, I would rather buy it from a company and have them do it for me for a higher price because I can afford to do so.

Do you see any hopeful signs of AMD turning the corner later this year with their upcoming Zen 16 core CPU and Polaris GPUs? Should I even bother to consider AMD at all at this point? How good are their support for GNU/Linux including Ubuntu 64 bit LTS GNU/Linux?

What else do I need to know?

Thanks.

---

### Post by Nuno_Abreu on 2016-02-08
AMD support for Linux should be a lot better, especially considering the latest GPUs - the CPUs are fine at this point.
Now, if you're trying to compare Intel to AMD, you should kind of forget it... I'm not a fanboy, but I consider Intel better simply because things are optimized for it. It all depends on what you want to do, though.

You could buy an AMD computer and be just fine - I have a laptop full of AMD goodness and it's great. AMD likes multi-core processors... You can find octacores easily on the market, even - but Intel is so heavily well supported that programs just run better and smoother with them if you're considering products with identical power. It's about core efficiency.

In my personal opinion, and as AMD is way cheaper than Intel, I find AMD superior for rendering and working on intensive video and photo editing, regardless of their driver support (proprietary drivers are poor, the open-source ones are getting much better).
I think these new processors will be great anyway - I just hope they don't have a direct effect on power comsumption and focus more on their efficiency and heat dissipation (got a lot better over the years too).
AMD is getting there - I hope it finally rivals Intel again.

My advice: consider AMD, seriously!

---

### Post by yoshii on 2016-02-08
I just recently purchased an AMD-based HP ENVY for use with 32-bit Ubuntu Studio v14.04.3 LTS.  Everything worked out fine once I had edited the BIOS to allow legacy mode so I could bypass UEFI.  Until I did that, I couldn't change the boot order.  But with the boot order changed, I could boot up the Ubuntu Studio LiveDVD, erase Windows, and install Linux.  

The main thing I had to worry about before buying the computer was to avoid nVidia graphics.  The ENVY has some kind of Radeon, and it's supported just fine by Linux.  So no problems with that.  

Everything with the computer is running fine.  The multiple cores are being seen and I haven't had any issues.  No kernel panics or anything.  

I kept a spare empty partition because I might try to dual boot with v16 LTS of Ubuntu Studio this April when it comes out.  I might try the 64-bit version.  
I use Wine a lot with 32-bit REAPER (a digital audio workstation).  Once I had implemented some standard tweaks, it ran fine.  Some tweaks I implemented were to disable file access logging (noatime), and to disable unneeded services such as samba and bluetooth and cups/printing.  I just don't use those at all.  

The thing that I like about HP desktops, is that they are well-cooled.

---

### Post by Welly Wu on 2016-02-08
Thank you for the replies thus far. I am curious about AMD technologies as stated earlier and I do not consider myself a member of the PC Master Race such that I would sneer and turn a blind eye away from AMD's next generation products. The AMD Zen CPU looks to be quite interesting as well as their Polaris GPUs. I was wondering if AMD made their own solid state disks yet? Does anyone know for sure? I know AMD makes their own gaming RAM. I just checked and AMD does make their own SSDs. They seem to be an all encompassing PC company. It looks really intriguing to get an all AMD gaming desktop PC towards the end of this year and it should be considerably cheaper than my 2015 ZaReason Zeto desktop PC system which is based on Intel and nVidia and Western Digital. I'll keep a close eye on these upcoming AMD products due later this year and I'll read the reviews from reputable PC enthusiast websites and digital magazines. This stuff is starting to look really interesting soon.

---

### Post by mastablasta on 2016-02-09
> **Welly Wu said:**
> Thank you for the replies thus far. I am curious about AMD technologies as stated earlier and I do not consider myself a member of the PC Master Race such that I would sneer and turn a blind eye away from AMD's next generation products. The AMD Zen CPU looks to be quite interesting as well as their Polaris GPUs. I was wondering if AMD made their own solid state disks yet? Does anyone know for sure? I know AMD makes their own gaming RAM. I just checked and AMD does make their own SSDs. They seem to be an all encompassing PC company. It looks really intriguing to get an all AMD gaming desktop PC towards the end of this year and it should be considerably cheaper than my 2015 ZaReason Zeto desktop PC system which is based on Intel and nVidia and Western Digital. I'll keep a close eye on these upcoming AMD products due later this year and I'll read the reviews from reputable PC enthusiast websites and digital magazines. This stuff is starting to look really interesting soon.

AMD CPU still slightly weaker than Intel (because stuff is intel optimized) but they also cost less. in short they still offer best "bang for the buck". Intel CPU runs better at the moment but this is mainly to various unfair practices (sales, hard code tampering...) where intel worked hard to hinder AMD and to make them look bad.

Situation is similar in GPU. This time it is nVidia that uses it's largest share to make people optimize their games for nvidia chips only and to hinder AMD. AMD GPU is better than intel but (linux) is worse than nVidia. however the good part is that opensource driver get's help from AMD and that AMD longeterm goal is to go almost fully opensource. they have a new intiative (GPUOpen) that is also going towards that goal. if i understand them they would retain ony a few features as closed soource that would be easier to manitain. the rest would go opensource. I am not really software expert but this is from various articles i read on this topic.

so while AMD drops it's official support. it then helps to move these legacy cards into opensrouce driver support. which should count for something. but on the other hand opensource doesn't retain all features available at closed soruce.

---

### Post by oldfred on 2016-02-09
Some comparisons for gaming:
 22-Way Comparison Of NVIDIA & AMD Graphics Cards On SteamOS For Steam Linux Gaming Oct 2015
[URL="http://www.phoronix.com/scan.php?page=article&item=steamos-22-gpus&num=1"]http://www.phoronix.com/scan.php?page=article&item=steamos-22-gpus&num=1
[/URL]
 The Extreme Cases Where A NVIDIA GTX 950 Can Outperform An AMD R9 Fury On Linux OpenGL
[http://www.phoronix.com/scan.php?page=article&item=nv-gtx950-fury&num=1](http://www.phoronix.com/scan.php?page=article&item=nv-gtx950-fury&num=1)

I get the impression that if a gamer, nVidia is better currently. If primarily for just about any other use you choose whatever you like, AMD or Intel for cpu and AMD or nVidia for video. 
And the newest Intel chips own video driver is as good or better as most end video cards of 5 or 6 years ago. Just not good enough for gaming, yet. 
So if cost is a consideration, you can use internal cpu's video.


[URL="http://www.phoronix.com/scan.php?page=article&item=steamos-22-gpus&num=1"]
[/URL]

---

### Post by Welly Wu on 2016-02-13
I would treat any Phoronix article with their Phoronix Test Suite benchmark results with a huge grain of salt. Their benchmark results often do not reflect real world performance and they are mainly designed for clean, reproducible, and open source friendly sharing of misinformation. For example, Michael Larabel cites that the nVidia Geforce GTX 970 is not much less powerful than a nVidia Geforce GTX 980 which is simply not true. He also states that the nVidia Geforce GTX Titan X is not that much more powerful than the nVidia Geforce GTX 980 in his PTS benchmark results. When I ran the PTS disk speed test, it clearly showed some very slow benchmark results using both HDDs and SSDs that don't reflect real world performance. Phoronix is just bunk and I tend to avoid that site like the plague. It's often times more useful and helpful to read mainstream Microsoft Windows benchmark results and extrapolate them given the current state of GNU/Linux affairs accordingly and just guess about the performance deltas for the same PC hardware component. Phoronix and the PTS in particular are very misleading in reporting benchmark results and I simply don't trust Michael Larabel's findings too often.

---

### Post by Welly Wu on 2016-02-13
I'll keep my eyes and ears open to the upcoming new AMD hardware like the Zen CPU and Polaris GPUs among other AMD PC hardware components. At some point in time in the next several years, AMD is going to have to design, manufacture, and sell winning products for die hard Intel and nVidia fanboys like myself to even give them more consideration in the future. Right now, my biggest concern is power efficiency and performance per watt to dollar ratios. AMD has ceded this fight years ago and they're about to mount a pretty aggressive battle with Intel and nVidia later this year to compete let alone win this long war campaign. I agree that AMD produces better bang for my buck at this current time, but I can well afford a more expensive Ubuntu 64 bit LTS GNU/Linux gaming desktop so AMD's appeal for performance to price ratio is waning on me. I don't like how AMD PC components run much hotter and require significantly higher watts and volts and amps to drive them properly which almost guarantees that liquid cooling to be a mandatory feature just to build or buy an AMD gaming desktop or laptop PC. Also, Zareason is the only GNU/Linux certified OEM that has two AMD desktop PCs currently available for sale and their prices are sky high for older AMD PC hardware components which makes it a tough sell for repeat customers like myself to consider them. I don't like building my own desktop PC and I much rather prefer to have an expert do the work for me and I'll gladly pay extra for those services including a multi-year warranty and lifetime technical support for GNU/Linux. AMD desktop PCs tend to require much more watts, amps, and volts to power and I'm concerned about my power consumption even though my apartment lease provides for 100% free utilities. I don't want my landlord to say something to me about a spike in my electrical costs in the future.

---

### Post by mastablasta on 2016-02-15
Phoronix test suite includes demos from games. you can use those demos independently it is just much easier to install and use them with the suite.

so if you have unreal engine demo and get certain result there then that means something. although many games state you need at least dual core something and certain GPu to run them or have it as recommended , yet the games would then run on my now 12 year old PC. how is that possible? because they run fine and look fine on medium settings and ebcause most (slightly older games) are nto really optimised for dual or quad core, but instead use only one core. which again is fine with me. in any case i agree realy world performance is different. 

to me i see some review how well it can run certain game and i get a feeling of how good the GPU is. note that i am usually not high end gamer but i do like to get the most i can with my limited resources. still i would say that these demos available in phoronix test suite do show some things. they can show if GPUs are very similar or far appart. and that is mostl ywhat i am interested in as i am not ready to pay 50 EUR more for 5 or 10% gain in performance.. most of the time is do not even see the difference on monitor due to my poor eye sight 

:p

---

### Post by yoshii on 2016-02-15
I wouldn't worry so much about power consumption.  I think even the worst offender computers don't use much wattage.  It's not like a refrigerator or air conditioner.  
Personally, my AMD ENVY (desktop) runs really noticeabley coolly and quietly.  I think for desktops they know what they are doing.  But laptops in general often run the risk of overheating because so much stuff is crammed into such a tiny package.

---

### Post by Welly Wu on 2016-02-15
What I like most about my 2015 ZaReason Zeto desktop PC is that it has an EVGA Hadron Air case and a 500 watt 80+ Gold Plus power supply unit. This makes for a compact and extremely powerful desktop PC, but ZaReason charges a premium for their product in order for it to be guaranteed to be compatible with current and future Ubuntu 64 bit GNU/Linux versions.

ZaReason states that the AMD FX 9590 CPU requires a 1,000 watt power supply unit and liquid cooling alone. The AMD Radeon R9 295X2 dual single card GPU requires 500 watts of power alone. They sell up to a 1,300 watt power supply for their Fortis Extreme 2 desktop PC. I was considering to purchase it at the time when I was shopping for my first GNU/Linux certified gaming desktop PC system, but I was hesitant about the increased power consumption and costs for less performance at that time.

AMD has to get their game together at this point or else it will be relegated to second or third place status forever. I am hoping their upcoming AMD Zen CPU and Polaris GPUs will change the game in their favor, but AMD has a long history of troubling setbacks and steep financial losses.

---

### Post by mastablasta on 2016-02-16
AMD is supplying all chips for PS4 and Xbox. I think they are still in the game...

---

### Post by P-I H on 2016-02-16
I'm very pleased with my AMD computer, that I built 2011.
CPU: AMD FX-8120 Eight-Core Processor clocked at 4 GHz
GPU: Radeon R9 380
PSU: Antec TruePower New 650W 80+Bronze
Computer Case: Antec Solo II
OS: Ubuntu Xenical Xerus, with AMDGPU powerplay enabled.
Games like Civ 5 and BioShock Infinite run OK.
When browsing it's silent.

I will follow the development of the  AMD Zen CPU to see if it is worthwhile to build a new one in the autumn.

---

### Post by MartyBuntu on 2016-02-16
To be fair, the AMD FX 9590 is considered an upper end *enthusiast* CPU...and there are plenty of NVIDIA graphics cards that are power hungry.

Personally, I go for a mix of AMD processors (bang-for-the-buck) and NVIDIA graphics cards (reliable Linux driver support) for my workstations.

I'm currently running an FX 8230e with a 550ti graphics card. My wife's workstation has an FX 6300 and a 750ti, which is a superb power-to-performance-ratio card.

---

### Post by mastablasta on 2016-02-17
well imagine if you have 4 PC's one for each family member and each draws over 1000W power. I mean you almost need industrial plug... LOL I am not even sure what this would od to my wiring, as living room and bedroom ar eon same fuse, so could  4000 W even work on same fuse? and I don't think the fuses have a lot of A. add a server to that and TV and TV box, lights.... it goes crazy.

so I will try to stay within 300 w usage max. I think there are descent systems available in that power usage range.

---

