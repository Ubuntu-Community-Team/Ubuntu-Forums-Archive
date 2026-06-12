---
title: "Building a new computer"
date: 2012-04-10
forum: The Cafe
---

### Post by Mazate on 2012-04-10
Howdy... I'm going to be building a new computer soon since my old one finally laid down its life after many years of loyal service.  Here's my issue, I'll be building it with the latest AMD processor (probably a 6 or 8 core) and latest motherboard & memory.  Yes, I realize that this is an overkill for a linux OS but I'm not doing it for performance but rather to keep my computer from being obsolete for a very long time.  In any case, will I have trouble getting Ubuntu to work with the latest and greatest stuff?  If so, would I be better off backing off on the high end stuff a bit to increase my chances of getting it to work well with Ubuntu?  Thanks in advance.

---

### Post by SemiExpert on 2012-04-10
As much as I like to root for the underdog, as much as I like the APU concept, as much as I like to save a buck, I'm inclined to go with Intel for my next desktop, if I go with another desktop.  For the last generation, the i5-2500K/Z68 seems to have been reigning champ for value and performance, but I'm waiting to see about Linux compatibility issues with Ivy Bridge and H77/Z77 motherboards.  I've had AMD systems, some better than others, but I am worried about future Linux compatibility, mostly because of the layoffs last year.

---

### Post by FatFrog on 2012-04-10
I'm running an AMD Phenom2 X6 (hex core) and I haven't had any problems. 11.10 did have some problems playing nicely with the ATI catalyst drivers in extended display mode, but a recent update solved that. That being said, I would still recommend an NVIDIA GPU as it seems to give less lip when trying to use the proprietary drivers, overall.

---

### Post by roelforg on 2012-04-10
> **FatFrog said:**
> I'm running an AMD Phenom2 X6 (hex core) and I haven't had any problems. 11.10 did have some problems playing nicely with the ATI catalyst drivers in extended display mode, but a recent update solved that. That being said, I would still recommend an NVIDIA GPU as it seems to give less lip when trying to use the proprietary drivers, overall.
Never got the second output to work on my nvidia in oneiric,
and it's config apps are broken and outdated.
To make use of the extra features (extra screen) you need to run nivdia-xconfig but it's generated one is horribly wrong.
Needed to ssh in to it from another pc to remove it and relaunch X11.

---

### Post by haqking on 2012-04-10
> **roelforg said:**
> Never got the second output to work on my nvidia in oneiric,
and it's config apps are broken and outdated.
To make use of the extra features (extra screen) you need to run nivdia-xconfig but it's generated one is horribly wrong.
Needed to ssh in to it from another pc to remove it and relaunch X11.

I run a Nvidia GTX 580 3GB just fine with extended display.

proprietary drivers were a sinch and then just choose twinview from the Nvidia control panel and that was it.

---

### Post by roelforg on 2012-04-10
> **haqking said:**
> I run a Nvidia GTX 580 3GB just fine with extended display.

proprietary drivers were a sinch and then just choose twinview from the Nvidia control panel and that was it.

It might have been a good idea to mention it was an older card...
nvidia-96 driver

---

### Post by wolfen69 on 2012-04-10
> **haqking said:**
> I run a Nvidia GTX 580 3GB just fine with extended display.

proprietary drivers were a sinch and then just choose twinview from the Nvidia control panel and that was it.

People will argue which one is better, but in my experience, nvidia has always done me proud. But, I didn't go out and buy something that *just came out*, or is older than dirt either. If you stay with mainstream nvidia cards, you should have no problems.

---

### Post by Bandit on 2012-04-10
Running a MSI Cyclone O/C nv460GTX... Love this card, NV Prop drivers was super easy install as always and performance is outstanding. Runs cool also, 33c on average and never gets above 40c on full load over hours of play. Dont think they make the 460 anymore, but IIRC the nv500 series is based on this gpu. Hope that helps.

BTW was just looking up new hardware for my new system this summer.. I need over 1575 BUCKS,, :cry:

AMD FX-8150 CPU
ASUS Sabertooth 990FX Mobo
CORSAIR Vengeance 16GB (4 x 4GB) DDR3 1600
CM GeminII S524 CPU Cooler
OCZ Vertex 4 512GB SSD
CM Storm Series Trooper Case
CM Silent Pro Gold Series 800w PSU

Add my Current 460GTX video card, plus  my 4x WD Caviar Blue 320GB drives (1.2TB / RAID Stripping) and BOOYAA!!



As far as being Over Kill for Linux.. I only run LINUX.. :D  But I run it in style..

---

### Post by CharlesA on 2012-04-10
Holy crap. I thought my server build was expensive, but it's only a quad core with 16GB RAM (and onboard video).

---

### Post by Bandit on 2012-04-11
> **CharlesA said:**
> Holy crap. I thought my server build was expensive, but it's only a quad core with 16GB RAM (and onboard video).

Yea I may drop the SSD since thats 700 bucks of it and just stick to my 4 drive raid array. I get really good speeds from it anyway. 300ish MB/s R/W on average.

---

### Post by CharlesA on 2012-04-11
> **Bandit said:**
> Yea I may drop the SSD since thats 700 bucks of it and just stick to my 4 drive raid array. I get really good speeds from it anyway. 300ish MB/s R/W on average.
Yikes! That is one expensive SSD.

---

### Post by morgan141 on 2012-04-11
> **Bandit said:**
> Running a MSI Cyclone O/C nv460GTX... Love this card, NV Prop drivers was super easy install as always and performance is outstanding. Runs cool also, 33c on average and never gets above 40c on full load over hours of play. Dont think they make the 460 anymore, but IIRC the nv500 series is based on this gpu. Hope that helps.

BTW was just looking up new hardware for my new system this summer.. I need over 1575 BUCKS,, :cry:

AMD FX-8150 CPU
ASUS Sabertooth 990FX Mobo
CORSAIR Vengeance 16GB (4 x 4GB) DDR3 1600
CM GeminII S524 CPU Cooler
OCZ Vertex 4 512GB SSD
CM Storm Series Trooper Case
CM Silent Pro Gold Series 800w PSU

Add my Current 460GTX video card, plus  my 4x WD Caviar Blue 320GB drives (1.2TB / RAID Stripping) and BOOYAA!!



As far as being Over Kill for Linux.. I only run LINUX.. :D  But I run it in style..

Why go for the AMD? Up until my latest build I have always used AMD processors. However, bulldozer was nothing short of a disaster. Whilst I appreciate that benchmarks aren't everything, take a look at this:

[http://www.anandtech.com/bench/Product/288?vs=434](http://www.anandtech.com/bench/Product/288?vs=434)

Needless to say, I strongly recommend getting either an i5 2500k, or wait for ivybridge which is just around the corner.

---

### Post by SemiExpert on 2012-04-12
> **morgan141 said:**
> Why go for the AMD? Up until my latest build I have always used AMD processors. However, bulldozer was nothing short of a disaster. Whilst I appreciate that benchmarks aren't everything, take a look at this:

[http://www.anandtech.com/bench/Product/288?vs=434](http://www.anandtech.com/bench/Product/288?vs=434)

Needless to say, I strongly recommend getting either an i5 2500k, or wait for ivybridge which is just around the corner.

 The argument of the i5-2500K/Z68 is indeed compelling, and not just in comparison to Bulldozer, but again Intel's own LGA 2011.  I'm waiting impatiently for Ivy Bridge myself, remembering the Linux compatibility issues that accompanied the Sandy Bridge launch in early 2011?

---

### Post by Bandit on 2012-04-12
> **morgan141 said:**
> Why go for the AMD? Up until my latest build I have always used AMD processors. However, bulldozer was nothing short of a disaster. Whilst I appreciate that benchmarks aren't everything, take a look at this:

[http://www.anandtech.com/bench/Product/288?vs=434](http://www.anandtech.com/bench/Product/288?vs=434)

Needless to say, I strongly recommend getting either an i5 2500k, or wait for ivybridge which is just around the corner.

Because this is more of what I am comparing [http://www.anandtech.com/bench/Product/434?vs=29](http://www.anandtech.com/bench/Product/434?vs=29)

or deciding to go with PhenII x6 vs FX 8 core. Intel isnt in my picture..
[http://www.anandtech.com/bench/Product/434?vs=203](http://www.anandtech.com/bench/Product/434?vs=203)

Then again with results like this maybe it should be... I will get back with you.. LOL :lolflag:

---

### Post by SemiExpert on 2012-04-12
> **Bandit said:**
>  Intel isnt in my picture..


 That's exactly how I felt about Intel after Pentium 4.  Times change.

---

### Post by Bandit on 2012-04-13
> **SemiExpert said:**
> That's exactly how I felt about Intel after Pentium 4.  Times change.

I kinda feel like were jacking the thread. But hopefully the feed back were tossing around will help the OP still figure out what he wants.

I did a huge price/performance comparison last night. The new Intels are looking much better then they did in the past. I really wouldnt mind getting a i7 Six core. But the biggest drawbacks to me is the motherboards. None of the ones I have researched fully support the features I am looking for in the boards. 

- FULL 6GB/s RAID 0/1/5 support on all the attached SATA drives. Not just two or 3 of the drives. Most seem to fall back to 3GB/s mode in RAID.. Bad bad bad turn off..

- Lot LOTS of USB slots and I want both frontal and back USB 3.0 attachments.

- Dont want any onboard video mess.. Period..

- Memory.. Dual Channel at least and min of 32GB Support.

The [ASUS Sabertooth]("http://www.asus.com/Motherboards/AMD_AM3Plus/SABERTOOTH_990FX/#overview") is looking like my choice of boards. If I could get an Intel i7 boards with everything 
this board has, I would be sold. But even the Sabertooth intel boards only have half of what this one does. Hence the dilemma.. :confused:

---

### Post by mamamia88 on 2012-04-14
Amd or intel both are going to be plenty fast for normal day to day operations.   Excuse me if I'm wrong but hasn't the amd socket remained pretty consistent for amd lately meaning you can maybe buy an amd motherboard right now and the next generation cpu will hopefully work on the motherboard you have?  Also top of line amd is around $300 compared to the  top of the line i7 at around $1000.  Personally even if a similar priced i7 is faster right now i would rather know that i have the best the company has to offer and i would never pay $1000 just for a cpu.    Spend the money saved on the cpu for an ssd. I'd probably go 8gb ram to be safe and it's relatively cheap nowadays.  Don't go overboard on gpu. If you can find a board with decent onboard graphics that also has room for a dedicated gpu in the future that would be idea.  Save money when you build it and when the onboard graphics aren't sufficient anymore you can just add a card.

---

### Post by SemiExpert on 2012-04-14
> **mamamia88 said:**
> Amd or intel both are going to be plenty fast for normal day to day operations.   Excuse me if I'm wrong but hasn't the amd socket remained pretty consistent for amd lately meaning you can maybe buy an amd motherboard right now and the next generation cpu will hopefully work on the motherboard you have?  Also top of line amd is around $300 compared to the  top of the line i7 at around $1000.  Personally even if a similar priced i7 is faster right now i would rather know that i have the best the company has to offer and i would never pay $1000 just for a cpu.    Spend the money saved on the cpu for an ssd. I'd probably go 8gb ram to be safe and it's relatively cheap nowadays.  Don't go overboard on gpu. If you can find a board with decent onboard graphics that also has room for a dedicated gpu in the future that would be idea.  Save money when you build it and when the onboard graphics aren't sufficient anymore you can just add a card.

 The problem with that theory is that very few cost savy enthusiasts are buying $1,000 i7 processors when the i5-2500K has been on sale for as little as $150 and the i7-2600K is currently on sale for as little as $200 at Microcenter?  Throw in the fact taht Z68 motherboards are going for as little as $70!

I really don't see any cost based arguement in favor of Bulldozer when you can buy a i7-2600K for $200.

---

### Post by CharlesA on 2012-04-14
> **SemiExpert said:**
> The problem with that theory is that very few cost savy enthusiasts are buying $1,000 i7 processors when the i5-2500K has been on sale for as little as $150 and the i7-2600K is currently on sale for as little as $200 at Microcenter?  Throw in the fact taht Z68 motherboards are going for as little as $70!

I really don't see any cost based arguement in favor of Bulldozer when you can buy a i7-2600K for $200.

I always find it funny when people bring up the "extreme edition" Intel chips. It might be me but I'm not going to fork over a grand for a CPU when I can get one for a third or a quarter of the price. Granted the i7 Extreme is a 6-core and my i7 2600K is a quad, but the price of a normal Intel 6-core is almost twice what I paid for my quad. Cost vs performance always has a trade-off.

---

### Post by mips on 2012-04-14
> **CharlesA said:**
> I always find it funny when people bring up the "extreme edition" Intel chips. **It might be me but I'm not going to fork over a grand for a CPU when I can get one for a third or a quarter of the price. **

Cost vs performance always has a trade-off.

I think most people subscribe to that logic.

People go for the price vs performance sweet spot. There is usually a certain point where prices start jumping drastically. Over here gamers mostly pick the 2500k CPU with a P or Z series MB for overclocking and pump the majority of their cash into a decent GPU. There is still a biggish jump from the 2500k to the 2600k over here but after the 2600k people lose interest due to pricing.

---

### Post by Bandit on 2012-04-14
> **SemiExpert said:**
> The problem with that theory is that very few cost savy enthusiasts are buying $1,000 i7 processors when the i5-2500K has been on sale for as little as $150 and .......
I really don't see any cost based arguement in favor of Bulldozer when you can buy a i7-2600K for $200.

> **CharlesA said:**
> I always find it funny ............ Cost vs performance always has a trade-off.

> **mips said:**
> I think most people subscribe to that logic.

People go for the price vs performance sweet spot.........

I agree and very much true. 

The AMD or Intel debate really isnt based on the CPUs, its the motherboards. Currently AMDs Northbridge/Southbridge chipsets are just more robust in their offerings and less buggy. Then Intel ones seem to limiting on their flexibility and usage.
So its more of a Intel Chipset -vs- AMD Chipset debate, the CPUs are both competitive and the Intel Core i7-3930K is relatively still a competitive price since it offered twice the overall performance of AMDs flagship FX-8150. Thus its twice the price, but twice the performance. If Intels offering was a hundred bucks more, then AMD would be the better choice. But here again, its the motherboards comparison thats seem to be driving the decision on this more then the CPUs themselves.

With all the intel boards I have seen, I can only get 2 SATA6GB/s Slots and the rest are 3GB/s. Also if you run them in raid, all default back to 3GB/s. Which is a huge turn off.
The AMD based boards though can run RAID0/1/5 and even 10 all at 6GB/s with no restrictions. Letting you run 2 SSDs in a stripped array then 2 or 3 other mechanical drives in RAID5/10. More performance where you really need it.

---

### Post by mips on 2012-04-14
> **Bandit said:**
> 
With all the intel boards I have seen, I can only get 2 SATA6GB/s Slots and the rest are 3GB/s. Also if you run them in raid, all default back to 3GB/s. Which is a huge turn off.
The AMD based boards though can run RAID0/1/5 and even 10 all at 6GB/s with no restrictions. Letting you run 2 SSDs in a stripped array then 2 or 3 other mechanical drives in RAID5/10. More performance where you really need it.

How important is this really to you? This makes absolutely no difference when you want to watch a HD movie etc etc etc. The only time this would matter is on your OS and opening apps etc. You are not going to get 6GB/s performance on any device out there unless you spend big $$$$ on a solid state device using SDRAM. No magnetic storage device is gonna come close to pushing those boundries, even SSDs will struggle.

The only logical choice in the current environment is to go Intel unless you are scraping for money in which case AMD would be a logical alternative.

I'm not a vendor fanboy, every single pc I built was AMD (early k6 series) and only recently I got my first Intel system (Q6600) and i don't see any benefit right now in going back to AMD.

---

### Post by Bandit on 2012-04-14
> **mips said:**
> How important is this really to you?...
Actually more important the the CPU upgrade its self. I am getting two OCZ Vertex4 SSDs that run 6GB/s. I really want to hit over 1000MB/s Data Reads and ruffly at least 400ish or more Writes. Read is more important, as its not going to contain my /home dir. My home dir will be placed on my current drives (4x WD Caviars) that I want to run raid 5 or 10 on if possible. Really want performance mirroring on those drives. The SSD Raid will just be stripped.
 
Basicly everything on the ASUS Sabertooth 990FX is what I want and is the biggest reason to upgrade. My current CPU is a Phenom 9850. Good performing chip, but I want to upgrade to something little faster. Also with the exception of my HDDs and video card. The rest of the system including PSU and Case I am giving to my daughter. She is turning 7 this year and that the age I started learning to program. So this would be an extremely nice start for a 2nd grader. I have an older WD Raptor 75Gig drive and an ATi Radeon 4650(i think) I am putting back in this for her and installing Ubuntu 12.04 on it for her.

---

### Post by Paqman on 2012-04-14
> **Bandit said:**
> I really want to hit over 1000MB/s Data Reads

Yegads. Any particular reason, or just because you can?

---

### Post by Bandit on 2012-04-15
> **Paqman said:**
> Yegads. Any particular reason, or just because you can?

Well it supposed to be the slowest link. But yea mostly because I can. However there is some test I am running I need it for. Needing to find out how much hardware I will actually need to for real time celestial navigation equipment based on placement of celestial bodies around a given point in space. So yea I would be going with Revo's if they had something better then the Sandforce controller.

---

### Post by morgan141 on 2012-04-15
> **Bandit said:**
> Actually more important the the CPU upgrade its self. I am getting two OCZ Vertex4 SSDs that run 6GB/s. I really want to hit over 1000MB/s Data Reads and ruffly at least 400ish or more Writes. Read is more important, as its not going to contain my /home dir. My home dir will be placed on my current drives (4x WD Caviars) that I want to run raid 5 or 10 on if possible. Really want performance mirroring on those drives. The SSD Raid will just be stripped.
 
Basicly everything on the ASUS Sabertooth 990FX is what I want and is the biggest reason to upgrade. My current CPU is a Phenom 9850. Good performing chip, but I want to upgrade to something little faster. Also with the exception of my HDDs and video card. The rest of the system including PSU and Case I am giving to my daughter. She is turning 7 this year and that the age I started learning to program. So this would be an extremely nice start for a 2nd grader. I have an older WD Raptor 75Gig drive and an ATi Radeon 4650(i think) I am putting back in this for her and installing Ubuntu 12.04 on it for her.

Unless something has changed recently, doesn't running ssds in raid disable TRIM? 

If this is an important issue to you, go for it. However, I think your goals will have absolutely no real life impact on performance. Yes benchmarks will look great, but the biggest performance boost will come from just running a single ssd. Hell I bet you wouldn't be able to tell the difference between an ssd running in SATA2 or SATA3. SSDs are faster than hard drives because of their seek times, not read/write speeds.

Bulldozers are slower, hotter, consume more power and are more expensive than equivalent intel models. Yes bulldozer will do you fine if you wanted to get it, but the i5 2500k will do it better and cheaper.

edit: Sorry I didn't see this.

> **Bandit said:**
> Well it supposed to be the slowest link. But yea mostly because I can. However there is some test I am running I need it for. Needing to find out how much hardware I will actually need to for real time celestial navigation equipment based on placement of celestial bodies around a given point in space. So yea I would be going with Revo's if they had something better then the Sandforce controller.

Can you give a few more details on this? I'm a physicist and it sounds quite interesting :), but I'm also interested in how this translates into a requirement for huge read/write speeds.

---

### Post by mips on 2012-04-15
> **Bandit said:**
> Actually more important the the CPU upgrade its self.
 
Basicly everything on the ASUS Sabertooth 990FX is what I want and is the biggest reason to upgrade.

Ok in that case it looks like AMD is your only option. I don't know of any Intel based boards with the same specs.

Edit: AMD will also be bringing out some higher performance FX series CPU in Q3. [http://en.wikipedia.org/wiki/Bulldozer_%28microarchitecture%29#2nd_Generation](http://en.wikipedia.org/wiki/Bulldozer_%28microarchitecture%29#2nd_Generation)

---

### Post by Bandit on 2012-04-15
> **morgan141 said:**
> Unless something has changed recently, doesn't running ssds in raid disable TRIM?
Yes, thats a huge reason I havent went to SSDs yet. However on the new OCZ Vertex 4 that use a Indilinx Everest 2 controller that has built in garbage handling via its own hardware. It still has TRIM support, but is not detrimental to the performance of the drive if not used on IE2 based SSDs.

> 
Bulldozers are slower, hotter, consume more power and are more expensive than equivalent intel models. Yes bulldozer will do you fine if you wanted to get it, but the i5 2500k will do it better and cheaper. 
Yea sadly I am aware of that. If I had a PhenII x6 I wouldnt be upgrading CPU's. But the CPU is only 1/3rd of my upgrade. Also running a 125w Phen 9850 I know all about heat, but my cooling setup will keep it far below overheating even when highly overclocked.

> 
Can you give a few more details on this? I'm a physicist and it sounds quite interesting :), but I'm also interested in how this translates into a requirement for huge read/write speeds.
I cant go into deep detail, but what I can say is that its a XML based database that keeps track of planetary bodies in a grid fashion....

---

### Post by morgan141 on 2012-04-15
> **Bandit said:**
> Yes, thats a huge reason I havent went to SSDs yet. However on the new OCZ Vertex 4 that use a Indilinx Everest 2 controller that has built in garbage handling via its own hardware. It still has TRIM support, but is not detrimental to the performance of the drive if not used on IE2 based SSDs.

 
Yea sadly I am aware of that. If I had a PhenII x6 I wouldnt be upgrading CPU's. But the CPU is only 1/3rd of my upgrade. Also running a 125w Phen 9850 I know all about heat, but my cooling setup will keep it far below overheating even when highly overclocked.


I cant go into deep detail, but what I can say is that its a XML based database that keeps track of planetary bodies in a grid fashion....

Well what can I say, fair enough I suppose! You seem to be more than aware of what you need and what you'll get from the AMD, so enjoy it :).

However, I think this is an important point for others reading this thread who are thinking about building a new pc. If you're not sure which is better, go intel. Their CPUs are better in every price bracket this generation and the motherboard limitations discussed above have basically no impact on even the most high end users.

Saying that, I love the llano chips :), their integrated GPUs are very impressive!

---

### Post by Skara Brae on 2012-04-15
Last summer, I built a new gaming PC. It has a Core-i5 2500k on an MSI P67A-GD65 and one ASUS Radeon HD 6870 "DirectCU". Quite conservative, as one can see. It runs fine (the hardware, that is; don't get me started about Windows...)

I read that the i7's Hyper-threading wouldn't make much difference, so I left the i7 2600 for what it was.

I am not a computer expert, nor am I a "n00b", but I find the Core-i5 an amazing CPU.

---

### Post by Paqman on 2012-04-15
> **Bandit said:**
> Well it supposed to be the slowest link.

Well yes, but not all tasks are limited by I/O. I'd be surprised if running SSDs in RAID0 sped up the majority of tasks noticably compared to a single SSD. You'd see the numbers if you benchmarked, but I don't think you'd really be getting much bang for your buck. The big jump is from HDD to SSD, adding more SSDs in parallel will suffer from quickly diminishing returns on a desktop.

---

### Post by CharlesA on 2012-04-15
> **Skara Brae said:**
> Last summer, I built a new gaming PC. It has a Core-i5 2500k on an MSI P67A-GD65 and one ASUS Radeon HD 6870 "DirectCU". Quite conservative, as one can see. It runs fine (the hardware, that is; don't get me started about Windows...)

I read that the i7's Hyper-threading wouldn't make much difference, so I left the i7 2600 for what it was.

I am not a computer expert, nor am I a "n00b", but I find the Core-i5 an amazing CPU.
I've got an i5 in my laptop and a Phenom II x4 in my desktop and they both perform splendidly.

---

### Post by SemiExpert on 2012-04-16
> **CharlesA said:**
> I've got an i5 in my laptop

 Arrandale or Sandy Bridge? 

> **CharlesA said:**
>  and a Phenom II x4 in my desktop and they both perform splendidly.

 AM2+ or AM3?

---

### Post by CharlesA on 2012-04-16
> **SemiExpert said:**
> Arrandale or Sandy Bridge? 



 AM2+ or AM3?
Probably Sandy Bridge, it's for an Intel 3000 HD chip.

The Phenom II is an AM3.

---

### Post by Bandit on 2012-04-18
I have been looking over the Intel line up. The i7-3930k looks promising. Yes its almost 600 dollars, but its twice as fast as a AMD FX-8150. The i7's are more of the enthusiast line, so I guess that fits me. I also have choosen ASUS Sabertooth X79 mobo along with 32GB of Corsair Vengence DDR2-1600 (2sets of 4x4GB pairs). RAID concerns I have thought over, existing 4 HDDs I have I will just use 2 of them, one for home and other for a backup. I will keep one spare and other will go in daughters system. For the system drives I will pair up a set of OCZ 128GB Vertex 4's using Disk Stripping to get max performance. The built in Indilinx controler should take care of garbage collection every hour own its own without any kernel help. Its sytem drive anyway so there should not be hardly any writing to those drives unless I am installing something. With 32GB of memory I dont see a need for a swap partition.. lol Gonna drop this all over in a Cooler Master Cosmos II full tower and power it all with a 1000watt CM Silent Pro bronze certified PSU. Total system cost is looking at about 2,158.00 plus shipping and tax.. Not counting my existing HDDs and NV 460GTX I am re-using. May have to add divorce charges to that as well, depending on how well this blows over with my wife.

CM 1000w Silent Pro Bronze PSU - 174.99
CM Cosmos II ATX Full Tower - 349.99
Intel i7-3930K 3.2(3.8GHz Turbo) Six Core CPU, LGA 2011 - 599.99
Asus Sabertooth X79 LGA 2011 Mobo - 319.99
32GB Corsair Vengeance DDR3-1600 1.35v (4x 4GB set, 16GB x 2 sets, $119.99ea) - 239.98
Corsiar H100 Water Cooler - 114.99
OCZ Vertex4 128 MB SSD(s) (x2 drives, 178.99 ea) - 357.98
$2,157.91 Total plus shipping handling and possible tax.

Eat dirt Alienware!!


PS, Gonna run Ubuntu 12.04LTS as my ONLY Operating System.. hehe

---

### Post by Shazaam on 2012-04-18
Back to the OP, one thing to look for is where the sata/ide ports are on any motherboards that you are looking at. Newer generations of video cards span the width of matx boards (some are longer). I didn't take that it into consideration when I upgraded so I had to get 2 right-angle low profile sata cables that fit under my GTX460.

---

### Post by Bandit on 2012-04-18
> **Shazaam said:**
> Back to the OP, one thing to look for is where the sata/ide ports are on any motherboards that you are looking at. Newer generations of video cards span the width of matx boards (some are longer). I didn't take that it into consideration when I upgraded so I had to get 2 right-angle low profile sata cables that fit under my GTX460.

This is a good point. Some have them plug from top, some from the side. Really helps to know what space restrictions you are going to face. Video cards, case size and drive placement.
I know on my CM Sniper case I am using now I had to have L plugs for the hard drives.

---

### Post by mips on 2012-04-19
> **Bandit said:**
> RAID concerns I have thought over, existing 4 HDDs I have I will just use 2 of them, one for home and other for a backup. I will keep one spare and other will go in daughters system.

PS, Gonna run Ubuntu 12.04LTS as my ONLY Operating System.. hehe

There's always the option of a dedicated raid controller card should you have to go down that road.

Don't you game in windows? In future I will be looking at running a Xen hyper visor that has hardware passthourgh for the GPUs. This way you can run windows as a VM with direct access to the gpus for gaming, the other default VM would be linux though that will get the most use.

---

### Post by Bandit on 2012-04-19
> **mips said:**
> There's always the option of a dedicated raid controller card should you have to go down that road.

Don't you game in windows? In future I will be looking at running a Xen hyper visor that has hardware passthourgh for the GPUs. This way you can run windows as a VM with direct access to the gpus for gaming, the other default VM would be linux though that will get the most use.
I actually wanted a dedicated raid controller to get the IOs off the system, but looks like the introduction of multicore CPUs there has been a decline in affordable hardware controlled raid cards. Now all I see is $300 adaptecs and they dont seem all that great for 300 bcuks.. :(

Nah I dont game anymore. Really havent had time for it the past two years. Would like the pass through for better Netflix viewing. :)

---

### Post by CharlesA on 2012-04-19
I've been using HighPoint Tech RAID cards in my server and they seem fairly decent. Might not have as many features are Adaptec, but they aren't as expensive (unless you want super high end)

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&N=-1&isNodeId=1&Description=highpoint+rocketraid&x=0&y=0](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&N=-1&isNodeId=1&Description=highpoint+rocketraid&x=0&y=0)

---

### Post by mips on 2012-04-19
> **CharlesA said:**
> Might not have as many features are Adaptec...

I'll be honest and say i'm not that impressed with Adaptec seeing I have some of their hardware. I'm sure there must be other alternatives out there from the likes of Intel etc

---

### Post by Bandit on 2012-04-19
> **CharlesA said:**
> I've been using HighPoint Tech RAID cards in my server ..........
Thanks for the heads up. I was looking to hardware raid controller. but looks like they have went up in price all around. Used to get a good entry level one for about 100 bucks. But even Highpoint ones now are up to 400 dollars. Guess its not as important now like they used to be when you was trying to offload as much as possible off your single core cpus. With 6 to 8 cores these days I dont think they are as much of a improvement as they used to be.

---

### Post by CharlesA on 2012-04-20
Probably not - I don't know if it's my imagination or what, but I the card I have (a 2640x1) handles just fine.

It worked fine what it was in the dual core and it just flys now that it is in the i7.

---

### Post by Fraoch on 2012-04-23
> **Shazaam said:**
> Back to the OP, one thing to look for is where the sata/ide ports are on any motherboards that you are looking at. Newer generations of video cards span the width of matx boards (some are longer). I didn't take that it into consideration when I upgraded so I had to get 2 right-angle low profile sata cables that fit under my GTX460.

And of course keep in mind many motherboards don't come with IDE support at all anymore if you have an older IDE hard drive or optical drive.  This seems to be mostly high-end motherboards but there are also some low-end ones without IDE ports as well.

Of course you can get IDE controller add-in PCI/PCIe cards but those are surprisingly expensive around here, much more than the difference between a low-end board without IDE and a midrange board with. Also I'd be wary of an older PCI IDE card, PCI links max out at 133 MB/s.  An older IDE hard drive won't saturate that but there are often onboard peripherals attached to the PCI bus that will steal away that bandwidth.  PCIe X1 has much more room, 250 MB/s for PCIe version 1.

---

### Post by Bandit on 2012-04-23
> **Fraoch said:**
> And of course keep in mind many motherboards don't come with IDE support at all anymore.......

LOL I havent noticed that until you said something about it.

IMHO I have noticed a rapid decline in quality of IDE DVD/CD Burners. I went through about 5 LiteOn and ASUS drives that where IDE. I switched to an SATA one and havent had any issues and been running same drive now for two years since I got it. Before I was switching them out ever 6 months..

---

### Post by Fraoch on 2012-04-24
> **Bandit said:**
> LOL I havent noticed that until you said something about it.

Yeah I forgot about it too then I went to select a motherboard and realized there was a problem.

My IDE drive probably only has a few years life left in it, I couldn't see any point wasting $25 on a PCI or $35 on a PCIe IDE card which would be useless after the drive dies.

---

