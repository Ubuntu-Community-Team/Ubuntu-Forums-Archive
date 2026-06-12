---
title: "help me pick a mobo"
date: 2007-02-20
forum: The Cafe
---

### Post by maniacmusician on 2007-02-20
I'm building myself another computer, and have basically picked out most of my parts. Now comes the most important one; the motherboard. It's a pretty hard pick, and I'm just exhausted from researching to get this far, so I wanted someone elses opinion. Here's what I've got so far (and am pretty set on buying):

> Case: [Antec LifeStyle SONATA II Piano Black Steel ATX Mid Tower Computer Case 450Watt SmartPower 2.0 Power Supply]("http://www.newegg.com/Product/Product.asp?item=N82E16811129155")

RAM: [G.SKILL 1GB 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400)]("http://www.newegg.com/Product/Product.asp?item=N82E16820231085")

Processor: [Intel Core 2 Duo E6600 Conroe 2.4GHz LGA 775]("http://www.newegg.com/Product/Product.asp?item=N82E16819115003")

Video Card: Already have a GeForce 7600GT

Hard drives: already have two 300GB SATA2 drives

The motherboard is really a pain in the *** to shop for. I was going to get a [GIGABYTE GA-965P-DS3 LGA 775 Intel P965 Express]("http://www.newegg.com/Product/Product.asp?item=N82E16813128012")...but the manual for that board says it only supports 1.8V RAM at 5-5-5 or 6-6-6 timings. The RAM that I've picked out runs at 2.1V with stock 5-5-5-15 timings, but can easily run stable at 4-4-4-12, which is what I was going to use.

So I need the following in a board:

> - Core2Duo compatible 
- at least one PCI-E slot 
- the ability to run the RAM I've picked (and obviously the ability to adjust the RAM timings)
- at least 1 IDE connector
- would prefer a firewire port, but it's not that important.

I think that's all. Help me out, **please.**

---

### Post by futz on 2007-02-20
> **maniacmusician said:**
> GIGABYTE GA-965P-DS3 LGA 775 Intel P965 Express[/URL]...but the manual for that board says it only supports 1.8V RAM at 5-5-5 or 6-6-6 timings.
I find that hard to believe (I think what they mean is "officially"). The DS3 is a stripped down (and not all that much) version of my GA-965P-DQ6. The DQ6 has **very good** overclocking and overvoltage controls in the BIOS. It's no DFI, but DFI BIOSes are mega overkill (I love them so much!). I'm pretty sure the BIOS on the DS3 is a pretty full subset of the DQ6 BIOS.

My DQ6 has controls for all memory timings and voltages, and there's plenty of headroom in the settings available. I run 2GB of Mushkin HP PC2-6400 at 4-5-4-11-1T and 2.1 volts. The machine overclocks great! 

And, unlike a couple of my buddy's boards, AHCI works fine. No problems at all setting it up. If you're installing Windows, be sure to build a F6 driver floppy first and have AHCI enabled before you start. If you forget, you have to do it after, which eats up some time doing a repair install of windows. Without AHCI, you don't get the benefits of your nice fast new SATA2 hard drive(s).

Here's a couple screenshots of the pertinent parts of the BIOS
[http://www.cluboverclocker.com/reviews/motherboards/gigabyte/GA-965P-DS3/p4.htm](http://www.cluboverclocker.com/reviews/motherboards/gigabyte/GA-965P-DS3/p4.htm)

Read that and google for some other reviews on the board - it's a popular one. I think you'll find that it will suit your needs just fine.

(One thing you may not catch on to right away with Gigabyte boards is that, when you enter the BIOS, you must hit CTRL-F1 to get Advanced Settings enabled. If you don't, you get the dumbed down version of settings.)

> - at least 1 IDE connector
Don't freak out, but the one IDE on the DS3 and DQ6 is provided by a JMicron controller. The ICH8 does not support IDE, so Gigabyte added the JMicron (badged as a Gigabyte chip) to provide one channel of IDE and another pair of SATA2 ports. 

I've come to the conclusion that the problem I was having installing with my IDE optical drive was my fault. I'm pretty sure it was working fine, but the installer stalls for a long time at 6%, and I thought it had crashed, and blamed it on the JMicron. If you're patient, it eventually continues, as I've since found on other installs.

---

### Post by maniacmusician on 2007-02-20
ah I see. So even though only 1.8 is officially supported, I should be fine with 2.1 or higher? good to know. A relief, actually, because I kind of liked this board.

I don't mind the JMicron controller...The issue was all patched up, and all updated kernels can deal with it just fine.

So if I'm good to go, I think I'll just wait a week or so until I've got enough cash, and go ahead with this order. I'm kind of excited; core 2 duo is going to be a fun ride.

---

### Post by tubasoldier on 2007-02-20
I would definitely look into mobos built by Intel. They usually have great support under Linux.

---

### Post by futz on 2007-02-20
> **maniacmusician said:**
> ah I see. So even though only 1.8 is officially supported, I should be fine with 2.1 or higher? good to know.
Yes. It will go a lot higher (enough to smoke your RAM, so be careful).

> A relief, actually, because I kind of liked this board.

I don't mind the JMicron controller...The issue was all patched up, and all updated kernels can deal with it just fine.

So if I'm good to go, I think I'll just wait a week or so until I've got enough cash, and go ahead with this order. I'm kind of excited; core 2 duo is going to be a fun ride.
I think you'll be very happy with it. I'm blown away by how fast mine is (same CPU as you). Fastest thing in the room (there's 9 machines and some junkers in here, some "were" pretty damn fast) at present.

I put Far Cry on the Windows partition and cranked all graphic detail (everything) to max and it plays great at 1680x1050. Smooth as can be. Video is a EVGA 7950-GT-KO.

---

### Post by futz on 2007-02-20
> **tubasoldier said:**
> I would definitely look into mobos built by Intel. They usually have great support under Linux.
Ya, but Intel boards are so boring. Who wants a board you can't overclock? Not me. Sure they're stable, but so bland.

Gigabytes are stable, feature-packed and overclock very well.

---

### Post by tubasoldier on 2007-02-20
Personally I would choose stability over getting a little fraction of speed.

---

### Post by maniacmusician on 2007-02-20
> **futz said:**
> Yes. It will go a lot higher (enough to smoke your RAM, so be careful).


I think you'll be very happy with it. I'm blown away by how fast mine is (same CPU as you). Fastest thing in the room (there's 9 machines and some junkers in here, some "were" pretty damn fast) at present.

I put Far Cry on the Windows partition and cranked all graphic detail (everything) to max and it plays great at 1680x1050. Smooth as can be. Video is a EVGA 7950-GT-KO.

ah well you do have a better card than I do. But I'm mainly just doing Beryl-ish kind of stuff, I don't play games that often...which is the reason I was able to trash my Windows partition, and go all-linux.

The main reason I'm upgrading is that I have a POS Celeron processor right now...it's got decent speed and everything, 3.4GHz clock speed, but it has a 256KB L2 cache! the P3's had twice that! Needless to say, this impacts me negatively. Especially recently, as I've started using VirtualBox for my VMing needs. VirtualBox relies heavily on cache to get the job done, and in that regard, this computer fails every expectation.

So I'm building that new computer, handing this one down to my parents (They're still using a Gateway Pentium II with Windows 2000; the ironic part is that my father is a DBA and really should be more on the up-and-up with technology). I'm really looking forward to the core 2 duo for several reasons...the 4MB cache is a gift in itself, but I'm really looking forward to the hardware virtualization, since the new kernel in Feisty actually takes advantage of it! 

When I build that computer, I expect my virtual machines to be fast enough that I don't really notice much difference between the host and guest OS's.

---

### Post by futz on 2007-02-20
> **tubasoldier said:**
> Personally I would choose stability over getting a little fraction of speed.
I get a good deal more than a "little fraction" :biggrin:
And it still runs rock-solid stable and with no heat worries.

---

### Post by maniacmusician on 2007-02-20
> **futz said:**
> I get a good deal more than a "little fraction" :biggrin:
And it still runs rock-solid stable and with no heat worries.
How easy is overclocking? I have to say, I have absolutely no experience with it. Since this processor and board are especially good for it, I've been thinking about trying it.

Wanna  help me out?

What do I need to take into consideration? Is all my hardware (RAM, video card, etc) capable of it? Or is a change of parts recommended? I really am pretty clueless when it comes to it. 

I remember reading somewhere that when you increase the processor clock speed, you have to increase the clock speed of other things as well, like your RAM, etc, and that they all limit each other in how high you can clock. RAM especially has limiting factors such as voltage and timings. but that's all I really know about it.

---

### Post by futz on 2007-02-20
> **maniacmusician said:**
> How easy is overclocking? I have to say, I have absolutely no experience with it. Since this processor and board are especially good for it, I've been thinking about trying it.
Nothin to it. The only thing you must remember is to keep good notes and change only one thing at a time. Every change you make should be thoroughly tested and documented, so you don't end up doing things multiple times or ending up with a machine that crashes randomly. Too big an overclock can corrupt hard drives, so you must test. Thorough testing is hideously time-consuming, but important.

> Wanna  help me out?
Surely.

> What do I need to take into consideration? Is all my hardware (RAM, video card, etc) capable of it? Or is a change of parts recommended? I really am pretty clueless when it comes to it.
Most decent mainboards will allow you to overclock the cpu and/or ram while locking the speed of stuff that isn't happy with higher clock rates, like video, etc. Anyway your RAM should OC fine, right? I've heard pretty good things about G.Skill.

You **MUST** carefully monitor temperatures of cpu, ram, chipsets and such. If things are getting too hot you have to back off until you can provide better cooling to the part(s) that are overheating. The Core 2 Duo's run nice and cool even with stock air cooling, but a good aftermarket cooler is always a good investment. I like Thermaltake's Big Typhoon - best air cooler there is IMHO!

> I remember reading somewhere that when you increase the processor clock speed, you have to increase the clock speed of other things as well, like your RAM, etc, and that they all limit each other in how high you can clock. RAM especially has limiting factors such as voltage and timings. but that's all I really know about it.
Partly true, but not all true with a good modern overclocking board like the DS3/DQ6 and many others. Generally you bump both cpu and ram together, but you can underclock the ram by choosing a lower multiplier if your cpu is capable of lots more. Or vice versa. I generally don't run at the raggedy edge tho. Just a nice healthy OC, well tested so it's still rock-solid stable. 

Those parts are gonna be obsolete in a few months anyway. Might as well use em to their true potential, right? :biggrin: But seriously, I've never smoked any parts doing it, and I've been overclocking computers since the 486 era. Every machine in this room (that's capable of it) is overclocked.

---

### Post by maniacmusician on 2007-02-20
I don't know if my RAM will be able to OC...It's got a CAS latency of 5, and 5-5-5-15 stock timings. Reading through the customer reviews, people have said that it runs rock-solid stable at 4-4-4-12. So what does it mean to lower the timings? I mean, I know what it does; but what effect does it have on the rest of the computer, and its ability to OC?

Since you've got the same processor that I'm looking at, and similar boards, clue me in. What did you to overclock your CPU? what clock speed are you running at now? What kind of cooling? Stock? Did you add anything special? 

I was planning to use Arctic Silver 5 cooling paste instead of the waxy goo that Intel puts on there, and I've heard that helps it stay a lot cooler. 

Overclocking is really intriguing, I want to understand it more, but it seems like all the articles I read about it get way too technical. I grasp about half of what they say and the rest goes over my head.

---

### Post by futz on 2007-02-20
> **maniacmusician said:**
> I don't know if my RAM will be able to OC...It's got a CAS latency of 5, and 5-5-5-15 stock timings. Reading through the customer reviews, people have said that it runs rock-solid stable at 4-4-4-12. So what does it mean to lower the timings? I mean, I know what it does; but what effect does it have on the rest of the computer, and its ability to OC?
You'll likely have to go back to 5-5-5-15 (that first 5 there is CAS Latency) or even higher numbers (looser timing) as you push the clock rate higher. Benchmarking will tell you where you're at and whether higher-clock-rate/looser-timing or lower-clock-rate/tighter-timing is better for your parts. Best quick benchmark for this kind of thing is super-pi. SiSoft Sandra for not-quick benchmarking, but you'd likely need windoze for that.

> Since you've got the same processor that I'm looking at, and similar boards, clue me in. What did you to overclock your CPU? what clock speed are you running at now? What kind of cooling? Stock? Did you add anything special?
I haven't really found the raggedy edge yet. Haven't had the time to get serious about it. I just boosted the main clock a little at a time until I arrived at my present, fairly conservative, setting of 280MHz. It will do more, but I need to find the time. At 280, with the 6600's 9 multiplier, that makes a 2520MHz CPU (stock is 2400) and since I have the memory multiplier set to Auto, memory is only at 840MHz. This Mushkin RAM should be capable of around 1000MHz or a bit better, so I have a ways to go. 

RAM gets **HOT** when you push it. I'll likely have to add a fan blowing directly on mine if I push it further. I have one of these:
[http://www.antec.com/Detail.bok?no=501](http://www.antec.com/Detail.bok?no=501) 
and if that doesn't do the job I have one of these standing by:
[http://www.ncix.com/products/index.php?sku=21240&vpn=CMXAF1&manufacture=CORSAIR](http://www.ncix.com/products/index.php?sku=21240&vpn=CMXAF1&manufacture=CORSAIR)

CPU cooling is stock for now. I have a spare Big Typhoon standing by if it's needed.

> I was planning to use Arctic Silver 5 cooling paste instead of the waxy goo that Intel puts on there, and I've heard that helps it stay a lot cooler.
Good heat transfer goop can't hurt, tho I'm not sure I believe all the great claims of the sellers. As long as you have something decent in there (even stock goop), you'll be ok. We run Arctic Silver Ceramique here in the swamp.

> Overclocking is really intriguing, I want to understand it more, but it seems like all the articles I read about it get way too technical. I grasp about half of what they say and the rest goes over my head.
Takes time and practice before you understand it all. Just reading about it is like reading about programming. It's all just words until you actually do it and see your code making it happen. Then it starts to make some sense. I'll dig ya up some good article links to help expand yer mind. :biggrin: PM me if I haven't got something posted by mid-tomorrow-night. That means I've forgotten.

---

### Post by maniacmusician on 2007-02-20
hah, thanks :) I can't really afford any aftermarket cooling devices at the moment, so I'll probably just go with the Arctic Silver and hope for the best when I finally decide to overclock.

A question, though: what kind of fan did your E6600 come with? I know there's one included. I'm asking because I'm using a PSU calculator to make sure that I have enough power from the power supply that I'm getting with my case. The case has a 120mm fan, and I think there's another 120mm fan in the PSU. So, what size fan does the processor use?

oh, and if you do decide to dig up those articles, thanks a lot in advance.

cheers

---

### Post by futz on 2007-02-20
> **maniacmusician said:**
> A question, though: what kind of fan did your E6600 come with? I know there's one included. I'm asking because I'm using a PSU calculator to make sure that I have enough power from the power supply that I'm getting with my case. The case has a 120mm fan, and I think there's another 120mm fan in the PSU. So, what size fan does the processor use?
Stock fan looks like an 80mm. Don't be shy about throwing more PSU than you need at it. You may be glad you did later. Stock supplied-with-case PSU's are notoriously bad, but that Antec should be decent quality, tho 450W is pretty minimal these days. At least with an Antec you can be sure you're getting an honest 450W out of it. I sure wouldn't build any but the smallest boxes with less.

And if you're going to overclock, you need solid power. Too much is perfect. Any starvation or dips and you're going to have trouble.

---

### Post by maniacmusician on 2007-02-20
well the PSU calculator tells me I need somewhere from 400-420 Watts...so the 450 should be fine right?

Normally I wouldn't mind buying a seperate PSU, but that case is so beautiful...and it'd be a shame to waste that power supply....

I dunno.

---

### Post by futz on 2007-02-20
> **maniacmusician said:**
> well the PSU calculator tells me I need somewhere from 400-420 Watts...so the 450 should be fine right?

Normally I wouldn't mind buying a seperate PSU, but that case is so beautiful...and it'd be a shame to waste that power supply....

I dunno.
Probably fine until you upgrade your video card. New big cards are power hogs!

Scroll up and re-read a few of my posts. I'm a mad editor. Hehehe. Added/changed a few details.

---

### Post by maniacmusician on 2007-02-20
haha yeah you are. must confuse people a lot :) (awesome fans by the way!)

okay, I think I'm enlightened for now. I'm tight on cash right now....sadly, it looks like my computing needs will determine my budget for about the next year! I'm going to buy these parts within a few weeks, they'll cost me about $650 US. 

Then in July, my parents are pitching in about $1,000 for a laptop...I'll also probably contribute about $1,000...and there goes most of my savings :) 

And then later on in the year, I'll upgrade this computer...with more RAM, of course, I'd always intended for a 2 GB minimum. I'll also hopefully get a new video card...an aftermarket cooler for my cpu....and a new PSU. That'll probably cost me another $400. 

Great, wonderful. Looking forward to watching my money melt away. lol.

---

### Post by futz on 2007-02-20
> I'll upgrade this computer...with more RAM, of course, I'd always intended for a 2 GB minimum
Here's the thing about RAM in modern mainboards. You want two sticks - not four. Two sticks will run at 1T timing. Four sticks forces you to 2T timing, which can cost you as much as 10 to 15% of RAM speed (maybe not that much, but you get the idea). You definitely want 1T if you can get it.

And you definitely want two sticks - not one, because RAM is accessed in dual channel mode when you have two sticks or four. Dual channel is like RAID0 for memory. RAM access is interleaved which makes memory I/O almost twice as fast. So on any mainboard that has dual channel memory access you should ALWAYS use matched pairs.

So if you're going to upgrade later, you'd be best to take out your two 512MB sticks (or two 256MB) and sell them off. Replace with a pair of 1GB sticks to get 2GB.

> Looking forward to watching my money melt away. lol.
Aint it great?!?! :mrgreen: The best way, if you can manage it, is to "surf" the backside of the wave. This does eat some money, but not as much, I don't think, as running each machine into the ground and doing a full replace every time. And you always have a fairly decent machine instead of the gradual-fade-to-worn-out-obsolete-junk/nice-new cycle.

Sell off stuff while it's still somewhat technically decent - you'll take a loss, but sell early so you don't take too bad a beating. Use the money to defray the costs of new replacement parts.

"Backside of the wave" means don't buy cutting edge (EXPENSIVE) parts. Buy good fast parts, but not the newest hottest. If possible, buy used from a friend ("idiot" hehehe - no, he's a great guy) who loves to surf further toward the bleeding edge of new stuff.

Sell typically to "family" types who don't need a smokin fast rig and are on a budget. They just want something good quality and solid that will last a few years, and they're sick of blowing big bucks for crappy name-brand package machines.

---

### Post by futz on 2007-02-20
Guess I should write my own overclocking guide. To my surprise, I didn't find any really complete tutorial or article.

This site used to be DFI-Street.com, but they had a fight with DFI and now they're
[http://www.diy-street.com/forum/index.php](http://www.diy-street.com/forum/index.php)
There's some decent info here, along with some misinformation at times. Like any forum. There are a few people at this forum who's answer to every problem is to get a new PSU. And then there's the guys who believe that if they keep the Clear CMOS jumper on for hours it will clear the CMOS better.:mrgreen: But it's not all sillyness. Worth reading.

Here's a link to their old Athlon and DFI mainboard overclocking guide. Parts of it are off topic for you, but there's lots of great info in there, especially in the BIOS section.
[http://www.diy-street.com/forum/showthread.php?t=20823](http://www.diy-street.com/forum/showthread.php?t=20823)

The rest of these I haven't read. Just googled around for anything that looked decent.
[http://www.sysopt.com/tutorials/article.php/12034_3608801_1](http://www.sysopt.com/tutorials/article.php/12034_3608801_1)
[http://www.overclock.net/intel-cpus/1567-intel-overclocking-guide.html](http://www.overclock.net/intel-cpus/1567-intel-overclocking-guide.html)
[http://www.atomicmpc.com.au/forums.asp?s=2&c=6&t=10706](http://www.atomicmpc.com.au/forums.asp?s=2&c=6&t=10706)
[http://www.xtremesystems.org/forums/showthread.php?t=114824](http://www.xtremesystems.org/forums/showthread.php?t=114824)

---

### Post by maniacmusician on 2007-02-21
alright, cool. Thanks.

---

### Post by flyingbrass on 2007-02-21
Antec power supplies seem to have gone downhill in quality over the past years.  I'd definitely use something other than the one included with that case.  Read the reviews in your Newegg link.  The PS is pretty bad.

Since you're not in a huge rush, keep an eye on some of the "deals" forums and sites for sales.  The Hot Deals forum at Anandtech is one example.

Core 2 Duo prices are supposed to be cut in April.  Can't tell where memory prices will go, but they've fallen a lot recently and are currently quite low.

---

### Post by maniacmusician on 2007-02-21
Actually, Antec did have a few shipments of faulty PSU's sent out, but they've since remedied the problem.

I guess I could wait until April unti Core 2 Duo prices are cut, but to be totally honest, I don't feel like waiting too much. At the moment, I'm calling in some money I've lent to people in the past. I should have about $500 coming my way soon, probably more, and I can afford to put up the rest myself, so I was thinking about ordering stuff within the next week or so.

How much are the C2D prices going to go down? unless we're talking price cuts of $100 on the E6600 (which seems extremely unlikely), I don't mind spending a little extra to get it sooner. Besides, people will scramble to get it once prices are down. So yeah, how big are these price cuts going to be?

Thanks for the tip about the hot deals forum. I'll sift through it. I'm pretty much set in what parts I want to buy, I just have to find the best prices for them and order. I don't want to change a part at the last minute and end up with something I didn't really want.

---

### Post by spockrock on 2007-02-21
I am a huge fan of DFI boards, I have the Lanparty NF4 Ultra-D (sorry I think SLI and crossfire is dumb) and the board, well the boards bios is jampacked with things you can tweak, sufficed to say I will probably only buy DFI boards hence forth, and they are killer overclockers......

---

### Post by maniacmusician on 2007-02-21
I'm not that much of a tweaker when it comes to hardware, so I think I'll be fine with the board I've chosen.  I might do a slight overclock later this year, if I have enough money to score some better parts.

---

### Post by spockrock on 2007-02-21
well I am not gonna lie, if you want a slight overclock stock hsf should be fine, just watch your temps, and of course make sure the oc is stable.  Aftermarket cooling is good if you wanna push your components to the limit, or if you want a cooler running component.  Granted the core2duos and the current A64's run really cool.  Also third party cooling is good if you want to undervolt your components as well.

---

### Post by futz on 2007-02-21
> **spockrock said:**
> I am a huge fan of DFI boards, I have the Lanparty NF4 Ultra-D
Me too, on both counts! But I think DFI is hurting financially. When I went shopping for a new board recently I found that they had fallen behind, and had no models that suited me. So I went back to my previous favorite - Gigabyte. The instant DFI has some new boards out I'm there again. Hope they survive.

> they are killer overclockers......
Yup. You have total control. What an amazing BIOS!

---

### Post by maniacmusician on 2007-02-21
> **spockrock said:**
> well I am not gonna lie, if you want a slight overclock stock hsf should be fine, just watch your temps, and of course make sure the oc is stable.  Aftermarket cooling is good if you wanna push your components to the limit, or if you want a cooler running component.  Granted the core2duos and the current A64's run really cool.  Also third party cooling is good if you want to undervolt your components as well.
I really don't want to overclock without aftermarket coolers. Decent air coolers aren't insanely expensive, and they're usually worth it to prolong the life of your processors. Also, the power supply I'm getting right now just barely covers my PSU needs (by about 50 Watts), so I'll definitely need to upgrade that when I overclock. I'd also consider upgrading my RAM and vide card at the same time.

---

### Post by futz on 2007-02-21
> **maniacmusician said:**
> I really don't want to overclock without aftermarket coolers.
Don't be too fearful about it. The C2D's run nice and cool, just like Athlon 64's. They're nothing like those crazy-hot P4 Prescotts. Those d@mn things were so hot that stock cooling couldn't keep em cool even at stock clock rates. I still run at least one (maybe 2) prescotts here still, so I'm not talkin out my @ss. :mrgreen:

Just keep an eye on temps and you'll be fine unless you mean to go for a huge OC. Start bumping voltages and clock rates sky high and you'll be lookin for some good cooling very soon.

---

### Post by maniacmusician on 2007-02-21
> **futz said:**
> Don't be too fearful about it. The C2D's run nice and cool, just like Athlon 64's. They're nothing like those crazy-hot P4 Prescotts. Those d@mn things were so hot that stock cooling couldn't keep em cool even at stock clock rates. I still run at least one (maybe 2) prescotts here still, so I'm not talkin out my @ss. :mrgreen:

Just keep an eye on temps and you'll be fine unless you mean to go for a huge OC. Start bumping voltages and clock rates sky high and you'll be lookin for some good cooling very soon.
well I'm not afraid exactly, but the cooler it is, the better. Hell I'd take phase-change cooling if I could afford it.

---

### Post by spockrock on 2007-02-21
> **futz said:**
> Me too, on both counts! But I think DFI is hurting financially. When I went shopping for a new board recently I found that they had fallen behind, and had no models that suited me. So I went back to my previous favorite - Gigabyte. The instant DFI has some new boards out I'm there again. Hope they survive.


Yup. You have total control. What an amazing BIOS!

yeah, right now I think the best board to get is the evga 680i sli board, from what I have heard it also has a bios thats great for tweaking......but I am happy with my computer right now, and waiting to see how K8L performs before I make any switches.  Hopefully DFI will get its act together, but DFI is the only one releasing the latest ATI chipset for the Intel cpus, which have been killer overclockers, but its seems the the Nvidia chipsets are preferred because of SLI over crossfire.  I think dual graphics is expensive and only of use if you buy the two highest end gpus on the market at the time......

> **maniacmusician said:**
> I really don't want to overclock without aftermarket coolers. Decent air coolers aren't insanely expensive, and they're usually worth it to prolong the life of your processors. Also, the power supply I'm getting right now just barely covers my PSU needs (by about 50 Watts), so I'll definitely need to upgrade that when I overclock. I'd also consider upgrading my RAM and vide card at the same time.

this is true, not all aftermarket coolers don't have to be expensive, right now I am running the freezer 64 from arctic cooling, and wow, at 2.6GHz I am sure my cpu is cooler then at stock speeds, and the stock cooler only let me hit about 2.4GHz.  That cost me around 40$(can) granted in my previous system, on my 2500+ XP Barton core, I paid I think 70-100$ for a thermalright heatsink, you can find good aftermarket coolers that are cheap, but ofcourse you pay extra if you want a thermalright or the best heatsink out there though...... there is also water or phase change cooling as well, which can get expensive as well.

---

### Post by maniacmusician on 2007-02-21
water cooling is just a messy affair, I hate having to deal with that. Wish I had phase change cooling, lol, but that's not happening. So I stick with air cooling whenever I can. 

Question; would you mind taking a glance at the stick of RAM that I've picked out (first post) and tell me if that's a good candidate for a bit of an overclock using the processor and motherboard I picked? Even if it isn't, I'll probably still buy it, I'm just curious, since I was planning on doing it eventually.

---

### Post by futz on 2007-02-21
> **maniacmusician said:**
> the stick of RAM that I've picked out
Did you read my little rant on dual-channel? Putting a single stick in that board harshly cuts your performance. Go for two.

I know, "I can't afford it!". You think you'll buy another later, but what happens when you go to buy and they've discontinued that ram and you can't find a match. Get a matched pair now, even if they're smaller, to fit yer budget. Just go for a pair of 512mb's.

Here's a review:
[http://techgage.com/article/g_skill_2gb_f2-6400phu2-2gbhz](http://techgage.com/article/g_skill_2gb_f2-6400phu2-2gbhz)

EDIT: Just finished reading the review. Not too shabby. Decent ram for the price.

---

### Post by spockrock on 2007-02-21
> **maniacmusician said:**
> water cooling is just a messy affair, I hate having to deal with that. Wish I had phase change cooling, lol, but that's not happening. So I stick with air cooling whenever I can. 

Question; would you mind taking a glance at the stick of RAM that I've picked out (first post) and tell me if that's a good candidate for a bit of an overclock using the processor and motherboard I picked? Even if it isn't, I'll probably still buy it, I'm just curious, since I was planning on doing it eventually.

its a good stick of ram, from what I have been reading, given the voltage you can get it to hit 1066 fsb speeds, and as futz said, dual channel is advantageousness because it literally doubles your memory bandwidth, from 64bits to 128bits, now that does not mean you'll get double the throughput but it does give the performance a nice kick.  Of course I mean you will see better performance if something uses more ram right.....I mean  if you aren't going to be say doing something too ram intensive you wont notice it, but if you do it could shave off seconds or increase your fps .......

---

### Post by futz on 2007-02-21
> **spockrock said:**
> if you aren't going to be say doing something too ram intensive you wont notice it, but if you do it could shave off seconds or increase your fps .......
You'll notice it. Everything a computer does is ram intensive. Software lives and works in ram. Make access almost twice as fast and it DOES make a big difference.

As an odd related example, I own a OCZ Rally dual channel usb stick. When it was new I took two of my friend's non-dual channel sticks (same size) and did some careful benchmarking with two large sets of files (1GB of large files and 1GB of small files). Sure enough, almost twice as fast.

---

### Post by flyingbrass on 2007-02-22
> **maniacmusician said:**
> How much are the C2D prices going to go down? unless we're talking price cuts of $100 on the E6600 (which seems extremely unlikely), I don't mind spending a little extra to get it sooner. Besides, people will scramble to get it once prices are down. So yeah, how big are these price cuts going to be?
Google turned this up: [http://www.madshrimps.be/vbulletin/showthread.php?t=30534](http://www.madshrimps.be/vbulletin/showthread.php?t=30534)

---

### Post by spockrock on 2007-02-22
> **futz said:**
> You'll notice it. Everything a computer does is ram intensive. Software lives and works in ram. Make access almost twice as fast and it DOES make a big difference.

As an odd related example, I own a OCZ Rally dual channel usb stick. When it was new I took two of my friend's non-dual channel sticks (same size) and did some careful benchmarking with two large sets of files (1GB of large files and 1GB of small files). Sure enough, almost twice as fast.

I also have a usb rally usb key, I think its flipping fast, but odd not 'fast' enough for vista readyboost, not like I would use that feature.  I love my rally, so so so much....

but back to dual channel vs single channel, I have seen benchmarks and I mean, the numbers are no where near 2x as fast, use it if you can, the best gains will be seen when, encoding/decoding, encrypting/decrypting.  I mean if dual channel were 2x in real world then AMD surely would of make skt 754 chips dual channel capable right?  yes, you theoretically have double the bandwidth, yes I do realize that everything sits in ram, but to take full advantage of the dual channel to give you have enough information to saturate single channel bandwidth, and how often is that?? I seriously do not think that a user will notice if they are running in dual channel or not.

Ok there is one way to check, when I feel not lazy, I will move on of the sticks of ram in my case and see if I can notice dual and single channel performance.

---

### Post by mips on 2007-02-22
> **maniacmusician said:**
> water cooling is just a messy affair, I hate having to deal with that. Wish I had phase change cooling, lol, but that's not happening. So I stick with air cooling whenever I can. 

Question; would you mind taking a glance at the stick of RAM that I've picked out (first post) and tell me if that's a good candidate for a bit of an overclock using the processor and motherboard I picked? Even if it isn't, I'll probably still buy it, I'm just curious, since I was planning on doing it eventually.

What ever happened to Peltier junctions for cooling, they were all the rage many moons ago and i actually had on on my k6 I think ?

Always go with 2 sticks of ram in a dual-channel MB.

---

### Post by futz on 2007-02-22
> **mips said:**
> What ever happened to Peltier junctions for cooling, they were all the rage many moons ago and i actually had on on my k6 I think?
Too high of power consumption, and too much trouble with condensation. They've got to be perfectly sealed and insulated, or else you damage things. They fell out of favor.

There is one company using a peltier to cool the water in a water-cooling system. They have a thermostat in it I guess to prevent getting below dew point or freezing. Seems to work well according to reviews.

---

### Post by maniacmusician on 2007-02-22
> **futz said:**
> Did you read my little rant on dual-channel? Putting a single stick in that board harshly cuts your performance. Go for two.

I know, "I can't afford it!". You think you'll buy another later, but what happens when you go to buy and they've discontinued that ram and you can't find a match. Get a matched pair now, even if they're smaller, to fit yer budget. Just go for a pair of 512mb's.

Here's a review:
[http://techgage.com/article/g_skill_2gb_f2-6400phu2-2gbhz](http://techgage.com/article/g_skill_2gb_f2-6400phu2-2gbhz)

EDIT: Just finished reading the review. Not too shabby. Decent ram for the price.

> **spockrock said:**
> its a good stick of ram, from what I have been reading, given the voltage you can get it to hit 1066 fsb speeds, and as futz said, dual channel is advantageousness because it literally doubles your memory bandwidth, from 64bits to 128bits, now that does not mean you'll get double the throughput but it does give the performance a nice kick.  Of course I mean you will see better performance if something uses more ram right.....I mean  if you aren't going to be say doing something too ram intensive you wont notice it, but if you do it could shave off seconds or increase your fps .......

So you're saying dual-channel is worth it in the long run even if you spend twice the money? I'm not sure about that...I mean, I can tell myself that I'll sell the two 512MB sticks later on, but I know I won't, I just never get around to it. 

If you guys are absolutely convinced that dual channel is worth that much I might do it. But I'd rather do this; if I have any money left over, just buy two sticks of the 1GB G.Skill RAM.

The critical question is, does that RAM and my mobo support dual-channel? I'll go check that right now. 

edit: my mobo supports it....there's no such thing as dual-channel ram is there? ](*,) So since my mobo supports it, I guess I might buy two of them...

---

### Post by maniacmusician on 2007-02-22
> **flyingbrass said:**
> Google turned this up: [http://www.madshrimps.be/vbulletin/showthread.php?t=30534](http://www.madshrimps.be/vbulletin/showthread.php?t=30534)
Thanks...wow that might be worth it....damn. I was really itching to have this system in my hands within the week.

---

### Post by spockrock on 2007-02-22
> **maniacmusician said:**
> So you're saying dual-channel is worth it in the long run even if you spend twice the money? I'm not sure about that...I mean, I can tell myself that I'll sell the two 512MB sticks later on, but I know I won't, I just never get around to it. 

If you guys are absolutely convinced that dual channel is worth that much I might do it. But I'd rather do this; if I have any money left over, just buy two sticks of the 1GB G.Skill RAM.

The critical question is, does that RAM and my mobo support dual-channel? I'll go check that right now. 

edit: my mobo supports it....there's no such thing as dual-channel ram is there? ](*,) So since my mobo supports it, I guess I might buy two of them...

nah I am saying this, 1 stick of ram = about the same as 2 sticks of 512MB.  dual channel is nice, if you got it use it.  If not its not much.  The thing is with ram to work in dual channel both sticks have to have the same timmings, and same frequency.....and yeah no such thing as dual channel ram really.........if you wanna go 1 stick and then 1 stick go ahead, its really up to you.  I am saying its a nice perk, but you wont notice the difference by much.

---

### Post by maniacmusician on 2007-02-22
> **spockrock said:**
> nah I am saying this, 1 stick of ram = about the same as 2 sticks of 512MB.  dual channel is nice, if you got it use it.  If not its not much.  The thing is with ram to work in dual channel both sticks have to have the same timmings, and same frequency.....and yeah no such thing as dual channel ram really.........if you wanna go 1 stick and then 1 stick go ahead, its really up to you.  I am saying its a nice perk, but you wont notice the difference by much.
and herein lies the problem; futz is saying almost the exact opposite of what you're saying.

So, who is right?

---

### Post by futz on 2007-02-22
> **maniacmusician said:**
> there's no such thing as dual-channel ram is there?
No, the memory doesn't care. But when you buy a matched pair, the memory company has supposedly picked pairs that match up well in timing & performance. That's the idea at least.

> and herein lies the problem; futz is saying almost the exact opposite of what you're saying
I don't totally disagree with spockrock. To tell the truth, I've never A/B tested with 1-stick/2-sticks, so he could well be correct. The difference might not be as great as I think.

But we all agree that by running one stick instead of two, you are definitely leaving easy to get performance on the table. The only question is how much. For me, any amount is too much. I'm paying for it - I want it all.

---

### Post by maniacmusician on 2007-02-22
True, but financial situations dictate the way that these things go. I guess if I have the money left over, I'll get the extra stick now instead of in a few months.

---

### Post by maniacmusician on 2007-02-23
Whooo, I took the plunge!

I ordered it all. The stuff in the first post (2 sticks of the RAM) and I also bought some Arctic Silver 5, which I hope will do me some good.

It came out to $769, which is a lot. I feel a little empty after spending all that, but I'm hoping that it'll be all better once I get the computer. Also, I do get a $50 rebate, so it'll end up being around $710. It'll be worth it, I hope.

---

### Post by futz on 2007-02-23
> **maniacmusician said:**
> Whooo, I took the plunge!

It came out to $769, which is a lot. I feel a little empty after spending all that, but I'm hoping that it'll be all better once I get the computer. It'll be worth it, I hope.
Haha. You'll be alright once you get the new toy hummin. :mrgreen:

I spent around double that amount on my last build, but it's all relative. I probably make more, so I spend more. If I can't afford a few relatively cheap toys, why work so hard?

---

### Post by maniacmusician on 2007-02-23
> **futz said:**
> Haha. You'll be alright once you get the new toy hummin. :mrgreen:

I spent around double that amount on my last build, but it's all relative. I probably make more, so I spend more. If I can't afford a few relatively cheap toys, why work so hard?
Yeah, exactly.

If I had the money, I would've spend a lot more. I would've gotten a better video card (have a GeForce 7600 right now), I would have gotten an LCD monitor, bigger hard drives (I have 1 300GB SATAII drive, and one 80GB IDE drive...I want to replace the latter with another SATA drive). I would have breached 1000 if I had the money to do so. 

But you're absolutely right. At least we get to fully enjoy our toys as Linux users. [sigh] I can't wait.

A couple of things, I'm worried about though.

1. the RAM. Everything I heard about Dual Channel sounds amazing. You or spockrock mentioned that I needed to have the same type of RAM at identical timing and voltage...well, I read in the reviews for the RAM I bought that it runs absolutely stable at 4-4-4-12 (rather than the stock 5-5-5-15 it comes at). If I run both of those identical sticks of RAM at 4-4-4-12, will I still be able to take advantage of Dual-channel?

2. Arctic Silver 5...There were a bunch of people that were dissatisfied with the product. Claimed it didn't make any difference, their temps increased, or that it wasn't worth the money. Is there any special trick to applying it? I know to follow the instructions on their site, but is there anything besides that, that could help me get the best out of it?

---

### Post by futz on 2007-02-23
> **maniacmusician said:**
> 1. the RAM. Everything I heard about Dual Channel sounds amazing. You or spockrock mentioned that I needed to have the same type of RAM at identical timing and voltage...well, I read in the reviews for the RAM I bought that it runs absolutely stable at 4-4-4-12 (rather than the stock 5-5-5-15 it comes at). If I run both of those identical sticks of RAM at 4-4-4-12, will I still be able to take advantage of Dual-channel?
Timing has no bearing on dual channel use. Makes no difference. At stock clock rate, you can probably tighten your timing that much, but don't count on it. There is some variation in parts. Just because someone else could do it doesn't mean yours will. And once you start bumping clock rates up, you will definitely have to loosen timings somewhat.

I believe that faster clock rate is better than tight timing, but only a benchmark will tell you for sure. If you can get both at the same time then yer laughin, but that's not likely. Faster clocks always need looser timing.

> 2. Arctic Silver 5...There were a bunch of people that were dissatisfied with the product. Claimed it didn't make any difference, their temps increased, or that it wasn't worth the money. Is there any special trick to applying it? I know to follow the instructions on their site, but is there anything besides that, that could help me get the best out of it?
Just follow their instructions. It does get better after a few days or a week of cooking time, so don't expect big things immediately. And I really doubt if all these fancy dancy goops are worth the money, but I buy em anyway. Is one fancy goop going to make a huge difference over any other? Not likely. Maybe a tiny difference... There's not much in there. It's just there to fill any gaps and make better thermal contact between heat spreader and heat sink. If things are right, it should be mostly mechanical contact with almost no goop at all.

---

### Post by maniacmusician on 2007-02-23
> **futz said:**
> Timing has no bearing on dual channel use. Makes no difference. At stock clock rate, you can probably tighten your timing that much, but don't count on it. There is some variation in parts. Just because someone else could do it doesn't mean yours will. And once you start bumping clock rates up, you will definitely have to loosen timings somewhat.

I believe that faster clock rate is better than tight timing, but only a benchmark will tell you for sure. If you can get both at the same time then yer laughin, but that's not likely. Faster clocks always need looser timing.

Well, normally I would be more wary, but there were multiple users that reported that it ran stable at the lower timings. At least about 20 users or so. I understand that I'd have to loosen them up if I wanted to overclock.

So what do you recommend I do when I get both sticks? Lower them both to 4-4-4-12 and see what happens?

> **futz said:**
> 
Just follow their instructions. It does get better after a few days or a week of cooking time, so don't expect big things immediately. And I really doubt if all these fancy dancy goops are worth the money, but I buy em anyway. Is one fancy goop going to make a huge difference over any other? Not likely. Maybe a tiny difference... There's not much in there. It's just there to fill any gaps and make better thermal contact between heat spreader and heat sink. If things are right, it should be mostly mechanical contact with almost no goop at all.

Ok, thanks. 

Just out of curiosity, what temp are the chips supposed to run at with the stock goop?

---

### Post by futz on 2007-02-23
> **maniacmusician said:**
> So what do you recommend I do when I get both sticks? Lower them both to 4-4-4-12 and see what happens?
Get everything running and squared away - install your operating systems and such, all with the BIOS settings on Auto. Stock clock rates, voltages and memory timings. Once you've got things settled, then you can tinker with memory timings and other stuff. 

Auto settings for RAM won't run it at the manufacturer recommended voltage, but at normal DDR2 voltage, and almost always will be very relaxed on memory timings. You can change voltage and timings to the ram's stock rated settings right away if you want. I found my Mushkin wasn't happy with even small overclocks till it got the manufacturer's rated 2.1V. 

Always run at least a couple passes of Memtest after making memory timing changes. To be as close to 100% sure as possible that you're stable at non-stock timings, voltage or clock rates, you should run Memtest overnight. You should not get ANY errors. None. Zero tolerance on errors!

A long run (24 hours?) of mprime torture test is also a good idea to be even more sure you're stable. Monitor your temps, at least for a while, while running mprime torture. Things will heat up some, and probably max out to as high as you'll ever see at those BIOS settings.

> Just out of curiosity, what temp are the chips supposed to run at with the stock goop?
CPU temps will typically range between 30C-45C at idle and 40C-60C under load. Much beyond 70C and you're approaching dangerous. I really don't want my cpu to exceed 60C under heavy load. If it does, I install a good aftermarket cooler (Thermaltake Big Typhoon). CPU's are rated for maximum 98C if I remember correctly (check with Intel to be sure). Go beyond that and you could be buying a new one.

---

### Post by spockrock on 2007-02-24
whoa, sorry to bump an old thread, but timings do make a difference, one because the memory controller cannot run two different sticks of ram at two different timings.  (I just helped a friend in montreal fix his computer instabilities, because his motherboard was running all the ram at 4-4-4-12 timings, while his newest stick of ram was 5-5-5-15.   Once he changed his ram timing values to 5-5-5-15, his computer was stable again.  So maniacmusician if you do get another stick of ram, try to get ram around the same timings...you do not have to but remember that you have to use the ram timing settings for the slower timing settings.

---

### Post by futz on 2007-02-24
> **spockrock said:**
> whoa, sorry to bump an old thread, but timings do make a difference, one because the memory controller cannot run two different sticks of ram at two different timings.  (I just helped a friend in montreal fix his computer instabilities, because his motherboard was running all the ram at 4-4-4-12 timings, while his newest stick of ram was 5-5-5-15.   Once he changed his ram timing values to 5-5-5-15, his computer was stable again.  So maniacmusician if you do get another stick of ram, try to get ram around the same timings...you do not have to but remember that you have to use the ram timing settings for the slower timing settings.
Didn't he say he decided to splurge and was buying the matched pair of 1gb sticks?

Ah, here it is:
> Whooo, I took the plunge!

I ordered it all. The stuff in the first post (2 sticks of the RAM) 
Anyway that's why I was pushing him to go for a matched pair. Mismatched pairs in dual channel can be not-so-good. You could have unpredictable results, as your friend in Montreal found out. Settings would have to be set for the "weakest link".

---

### Post by spockrock on 2007-02-25
wow, I look like an idiot, lol, hahahhaha >_<

---

### Post by maniacmusician on 2007-02-25
:) it's cool. Hopefully I'll end up running the pair at 4-4-4-12, after making sure it runs stable at stock, as futz said. 

[sigh] parts still aren't here. And we're due for a snowstorm tomorrow, so probably not then either. Bummer. Can't wait to get my hands on that stuff.

---

### Post by maniacmusician on 2007-02-26
I have all of the parts except for the case! They screwed up on shipping and now I have to wait another two days for it to get here! It's cruel to dangle it in front of me like that.

[settles in to wait]

---

### Post by spockrock on 2007-02-27
damn that must be frustrating.....

---

### Post by mips on 2007-02-27
> **maniacmusician said:**
> I have all of the parts except for the case! They screwed up on shipping and now I have to wait another two days for it to get here! It's cruel to dangle it in front of me like that.

[settles in to wait]

Lol, if the MB was a gigabyte the box could actually be turned into a assembly platforms. I was really impressed with the box but never used it as such. had all the cutouts etc so you could get the system going without a case.

---

### Post by maniacmusician on 2007-02-27
:) yes I probably could, but then I'd have to take some of it apart again when the case got here. Besides, the PSU is with the case as well.

---

### Post by mips on 2007-02-27
> **maniacmusician said:**
> :) yes I probably could, but then I'd have to take some of it apart again when the case got here. Besides, the PSU is with the case as well.

hmm, then you are fooked ;)  (Isn't Austin Powers great ?)

---

### Post by WalmartSniperLX on 2007-02-27
Asus P5B-Deluxe (intel P965 chipset). Check it out. Its pretty good. But I think Gigabyte (for some reason, and shown by benchmarks) works best with the core 2 duo. But thats just my opinion. I bought the Asus P5-Deluxe for my dads computer and it works great with a lot of useful tools and options in the bios. And, like all Asus boards, it balances performance with extreme stability.

(sorry if I came in a little off subject, I just skimmed the thread real fast so I could get my 2 cents in)

---

### Post by maniacmusician on 2007-02-27
Yeah, you'er a little late. If you skim the previous page, you'll see that I've already ordered. I have almost everything, just waiting for the damn case to get here. Should be here tomorrow, hopefully.`

---

### Post by maniacmusician on 2007-02-28
ok, I got this bad boy and threw it together, but I think I'm having some problems, one of which may be my drive set up. This is the way I have it right now:

> 
IDE: 
  Master: CD/DVD-RW
  Slave: 80GB IDE drive
SATA: 
      320GB drive
It sees the SATA drive as being on IDE channel 1 and the two IDE drives as being on IDE channel 4. The BIOS seems to lump the SATA and IDE together into one category?

I can't boot into my old installation because the places of the hard drives have changed and grub doesn't know what's what anymore. 

When I try the GParted Live CD, I just get a kernel panic, so I can't use that either. I can't find my feisty Herd4 disc.

I was about to reinstall Edgy, but I decided to mess around with the BIOS a little (no overclocking or anything, just basic settings) and now, the Edgy CD can't see my SATA drive.

Really tired now, so I'm going to bed; what should I do about this? I'd be fine with rearranging some stuff on the SATA drive and eliminating the IDE drive for now, but I can't even partition that drive. It's ridiculous. 

I think I'll have to start a support thread about this in General Help or something.

---

### Post by mips on 2007-03-01
I had a similair problem. In my BIOS I could 'order' the drives if I'm not mistaken.

My sugestion would be to install the SATA drive first. The have the PATA drive followed by the CD/DVD rom drive. If you have enough connectores connect the Pata & CD to a different BUS (assuming you have ide1, ide2 )

Mirror the contents of the old drive onto the new one.

You can also edit grub and change the drive numbers to boot of the correct drive.

Me, I would just reinstall from scratch. Does not take long.

---

### Post by maniacmusician on 2007-03-01
> **mips said:**
> I had a similair problem. In my BIOS I could 'order' the drives if I'm not mistaken.

My sugestion would be to install the SATA drive first. The have the PATA drive followed by the CD/DVD rom drive. If you have enough connectores connect the Pata & CD to a different BUS (assuming you have ide1, ide2 )

Mirror the contents of the old drive onto the new one.

You can also edit grub and change the drive numbers to boot of the correct drive.

Me, I would just reinstall from scratch. Does not take long.
true enough. I have no problem with reinstalling, except I changed some settings in the BIOS and now the installation CD can't see my SATA disk :) The problem here is, I use the PATA drive as /, and the SATA drive is divided up into partitions of /home/[user] and my music collection. I guess I could install everything onto the PATA drive as a one-time thing.

Anyways, I just need to figure out what the problem is. Need to read up on my BIOS and whatnot. 

Question: On the mobo, I didn't plug anything into the "SYS_FAN" space. Subsequently, no "System Fan" shows up in the BIOS. that's not a problem is it? I just couldn't find any fan-related wires that would fit there.

---

### Post by futz on 2007-03-01
> **maniacmusician said:**
> ok, I got this bad boy and threw it together, but I think I'm having some problems, one of which may be my drive set up. This is the way I have it right now:


It sees the SATA drive as being on IDE channel 1 and the two IDE drives as being on IDE channel 4. The BIOS seems to lump the SATA and IDE together into one category?

I can't boot into my old installation because the places of the hard drives have changed and grub doesn't know what's what anymore. 

When I try the GParted Live CD, I just get a kernel panic, so I can't use that either. I can't find my feisty Herd4 disc.

I was about to reinstall Edgy, but I decided to mess around with the BIOS a little (no overclocking or anything, just basic settings) and now, the Edgy CD can't see my SATA drive.

Really tired now, so I'm going to bed; what should I do about this? I'd be fine with rearranging some stuff on the SATA drive and eliminating the IDE drive for now, but I can't even partition that drive. It's ridiculous. 

Your problem is that you haven't enabled AHCI. Turn it on and the drives will not appear as IDE (they're emulating IDE at present). Switching to AHCI not only gives you all the SATA2 performance goodies, but cures a bunch of strangeness with Linux.

I've got no time to type details right now. If you haven't got it figured out by when I get home from work tonight, I'll give you details.

> I had a similair problem. In my BIOS I could 'order' the drives if I'm not mistaken.
The problem is not drive priority.

---

### Post by futz on 2007-03-01
> **maniacmusician said:**
> Question: On the mobo, I didn't plug anything into the "SYS_FAN" space. Subsequently, no "System Fan" shows up in the BIOS. that's not a problem is it? I just couldn't find any fan-related wires that would fit there.
Doesn't matter. When you put an exhaust fan in the back of the case you plug it in there. Or any other fan you'd like to monitor...

---

### Post by maniacmusician on 2007-03-01
I'm pretty sure I do have AHCI enabled. It was in the Integrated Peripherals menu I believe (I'm not at home either so speaking from memory here), and I think it was the first item on the menu. The two choices were Disabled and AHCI. After reading your first post in this thread, I thought it'd be better to turn AHCI on, so I did.

There was another option on the menu, right below it...something about Native IDE vs Legacy IDE. I changed that option to Native, and I think that's when it stopped working...but I think I switched it back and it still didn't work.

to be honest, I'm stoked that I even got it to POST. I'm sure I'll clear this thing up in good time as well.

---

### Post by futz on 2007-03-01
> **maniacmusician said:**
> I'm pretty sure I do have AHCI enabled. It was in the Integrated Peripherals menu I believe (I'm not at home either so speaking from memory here), and I think it was the first item on the menu. The two choices were Disabled and AHCI. After reading your first post in this thread, I thought it'd be better to turn AHCI on, so I did.

There was another option on the menu, right below it...something about Native IDE vs Legacy IDE. I changed that option to Native, and I think that's when it stopped working...but I think I switched it back and it still didn't work.

to be honest, I'm stoked that I even got it to POST. I'm sure I'll clear this thing up in good time as well.
Home from work for a quick sec... If you're seeing the drives listed as IDE devices then you probably do not have AHCI enabled. There are three options in that setting (possibly 2 on the DS3 - DQ6 has 3) - Disabled (IDE emulation), RAID and AHCI. 

Below that is SATA Port 0-3 Native Mode. Should be enabled.

If AHCI is enabled, you'll see no SATA drives listed after POST (in the IDE device list), but the next screen it jumps to will be Serial ATA AHCI BIOS, where it will delay a bit and then detect all SATA devices (a bit slowly).

Of course I'm assuming the BIOS is a subset of the DQ6 BIOS. They may have made more changes than I think (if this is the case I'll have to download the manual and have a look)...

I hope they haven't done what Asus did for some of their boards. We've been unable to get AHCI to work properly on them. Tried absolutely every possible combination of options, and the only thing we can think of is that there's a problem in the BIOS code. Of course nobody will admit anything, even tho they're unable to tell us how to get it to work. (P5B - Deluxe WiFi and Stryker Extreme we've had trouble with).

---

### Post by maniacmusician on 2007-03-01
I'll try those settings again when I get home.

It's very convenient to get help from you since we have almost identical boards. well, convenient for me :)

---

### Post by spockrock on 2007-03-01
sorry I can't help you with your board and bios settings but as another member mentioned, you can edit your grub settings, by pressing e, on the operating system that you wanna edit.

---

### Post by maniacmusician on 2007-03-01
> **spockrock said:**
> sorry I can't help you with your board and bios settings but as another member mentioned, you can edit your grub settings, by pressing e, on the operating system that you wanna edit.
too late, I already over-wrote that installation...

futz: I got home and dove into the BIOS...the settings were already as you said they were supposed to be. AHCI and Enabled for the Native thing. The reason that I don't have the raid option is because on the mobo, there are 2 SATA slots that are controlled by the Gigabyte controller that provide RAID. The other 4 controllers (the yellow ones) are controlled by the ICH8 chipset and don't provide RAID. Those are the ones that I'm using. 

But anyways. It still doesn't see my SATA drive AT ALL from the installation CD. I think its still visible from the BIOS though. 

Worse off than that, is this: I went ahead and installed a new system on the 80GB hard drive, including a new home dir and stuff. I tried to boot into it...but then it gave me the "Signal Not Found" error...meaning that the video card was failing to communicate with the monitor. why would my card not work in the OS? I think that may be because I set a resolution that was too high? Shouldnt it just default to a lower one? I'll try lowering it and seeing what happens.

Anyways, A bit of a mess. I'm wondering if I didn't up something wrong on the mobo.

edit: Actually, the BIOS doesn't even detect the SATA drive anymore....loose connection? I'll look into it..

---

### Post by maniacmusician on 2007-03-01
I don't get it....the drive is powering on, and the connector isn't loose. I even tried replacing the cable...nothing. This drive had better not be dead, because it's pretty damn  new, and it has ALL of my data on it. about 200 GB worth. 

The worst part is, it was working just yesterday,...wtf happened? The BIOS isn't even seeing it now. 

I  better not have lost this hard drive. At least it's not showing any of the symptoms. It's running very smoothly. It clicks a **little** bit at boot, but I think it's always done that. Then it resumes smooth, quiet operation.

---

### Post by futz on 2007-03-01
> **maniacmusician said:**
> I got home and dove into the BIOS...the settings were already as you said they were supposed to be. AHCI and Enabled for the Native thing. The reason that I don't have the raid option is because on the mobo, there are 2 SATA slots that are controlled by the Gigabyte controller that provide RAID. The other 4 controllers (the yellow ones) are controlled by the ICH8 chipset and don't provide RAID. Those are the ones that I'm using.
Ok.

> It still doesn't see my SATA drive AT ALL from the installation CD. I think its still visible from the BIOS though.
edit: Actually, the BIOS doesn't even detect the SATA drive anymore....loose connection? I'll look into it.
Hmm... That drive isn't jumpered for SATA1 is it? That shouldn't matter, but maybe check that. 

Try it in IDE mode. You can always fight with the AHCI setup later, and IDE mode isn't *too *much slower.

> Worse off than that, is this: I went ahead and installed a new system on the 80GB hard drive, including a new home dir and stuff. I tried to boot into it...but then it gave me the "Signal Not Found" error...meaning that the video card was failing to communicate with the monitor. why would my card not work in the OS? I think that may be because I set a resolution that was too high? Shouldnt it just default to a lower one? I'll try lowering it and seeing what happens.
How could you have set any resolution at all if you couldn't even get it to boot? It usually defaults to a terribly lame 1024x768 or 800x600 or something, with a very low scan rate. They want it to be sure to work first time if possible. You may have to run 'sudo dpkg-reconfigure xserver-xorg' (or just edit your xorg.conf) and set the driver to VESA to get things going. Then get a real NVidia driver in there asap, cuz vesa is S...L...O...W...

> Anyways, A bit of a mess. I'm wondering if I didn't up something wrong on the mobo.
Fun, huh? I remember the day I first fired up my nice new DFI board. It was set to basically all default settings. It wouldn't even try to boot. Just POSTed and crapped out. I spent a whole day tinkering with settings (I was an AMD noob at the time - ran only Intels before that) to get it going.

Umm... One more thing. How many hard drives? If more than one, I may have been too quick to dismiss that other guy's Boot Priority suggestion. If only one drive the bios doesn't have to try too hard to guess the right one.

---

### Post by futz on 2007-03-01
OH! OH! OH! OH! I just thought of something! That board has an ICH8, not an ICH8R? Is that correct? No RAID except that supplied by the JMicron?

If I remember correctly, the ICH8 doesn't do AHCI. That sounds wrong, but I have a foggy memory of reading that somewhere. But then why is there an AHCI option in the bios for the ICH8? Ok, I'm confused. I'll go look right now.

---

### Post by maniacmusician on 2007-03-01
> **futz said:**
> Ok.


Hmm... That drive isn't jumpered for SATA1 is it? That shouldn't matter, but maybe check that. 

No, because I was getting SATAII speeds with this hard drive when in my old computer. There's no jumpers in there at all, actually.

> **futz said:**
> 
Try it in IDE mode. You can always fight with the AHCI setup later, and IDE mode isn't *too *much slower.

To do that, I just set the AHCI to "Disabled" and the Native Mode to Disabled?

> **futz said:**
> 
How could you have set any resolution at all if you couldn't even get it to boot? It usually defaults to a terribly lame 1024x768 or 800x600 or something, with a very low scan rate. They want it to be sure to work first time if possible. You may have to run 'sudo dpkg-reconfigure xserver-xorg' (or just edit your xorg.conf) and set the driver to VESA to get things going. Then get a real NVidia driver in there asap, cuz vesa is S...L...O...W...

Well technically speaking, it does boot into it, but it just shows a "signal not found" which means the video driver is not working.

And I set the resolution during the install (text install). When it installs xserver-xorg, it gives you some resolutions to choose from. I chose 1600x1200, 1400x1050, 1280x1024, and left the rest as default.
> **futz said:**
> Fun, huh? I remember the day I first fired up my nice new DFI board. It was set to basically all default settings. It wouldn't even try to boot. Just POSTed and crapped out. I spent a whole day tinkering with settings (I was an AMD noob at the time - ran only Intels before that) to get it going.

heh :) I don't mind tinkering, as long as it ends  up working. If my $770 were spent in vain, then I may just have to kill someone.

> **futz said:**
> Umm... One more thing. How many hard drives? If more than one, I may have been too quick to dismiss that other guy's Boot Priority suggestion. If only one drive the bios doesn't have to try too hard to guess the right one.
I know it's not boot priority; it's the fact that the BIOS doesn't even see the SATA hard drive. In fact, one of the first things I did when  booted into the BIOS setup was to **change** the boot order and put my slave IDE hard drive as the first HD to boot from, because that's where my OS was. and it still detected the SATA drive for a little while after that. but, I'll repost about how I have the drives set up:

> 
IDE: 
  Master: CD/DVD-RW
  Slave: 80GB IDE drive
SATA: 
      320GB drive


Anyways, I'll try going back to IDE mode and see what happens. Got a bad feeling though.

---

### Post by maniacmusician on 2007-03-01
okay, it shows up after going back to IDE mode. 

When I go into recovery mode to edit my xorg.conf, my keyboard doesn't work...the Num Lock light is on, but I can't get a reaction out of the computer.

I think its because the BIOS forces a numlock=on. So i have to find that and put it back to normal.

---

### Post by futz on 2007-03-01
> **maniacmusician said:**
> No, because I was getting SATAII speeds with this hard drive when in my old computer. There's no jumpers in there at all, actually.
Actually, there are pins at least. There may not be a jumper on em tho. :mrgreen: All SATA2 drives are backward compatible with SATA1 if you jumper the right two pins.

> To do that, I just set the AHCI to "Disabled" and the Native Mode to Disabled?
AHCI-disabled switches to IDE emu mode. The difference between Legacy IDE and Native IDE I don't know, but it sounds like Legacy is the safe setting and Native is the better setting if it works. I could be wrong. Legacy is default.

> Well technically speaking, it does boot into it, but it just shows a "signal not found" which means the video driver is not working.

And I set the resolution during the install (text install). When it installs xserver-xorg, it gives you some resolutions to choose from. I chose 1600x1200, 1400x1050, 1280x1024, and left the rest as default.
Oh ya! Big duh from me. Now I remember.

> it's the fact that the BIOS doesn't even see the SATA hard drive. In fact, one of the first things I did when  booted into the BIOS setup was to **change** the boot order and put my slave IDE hard drive as the first HD to boot from, because that's where my OS was. and it still detected the SATA drive for a little while after that. but, I'll repost about how I have the drives set up:
The bios won't show the drive in the IDE list if you are in AHCI mode. And that second page I was talking about may not even show on a non-raid bios. They may not have even put that piece of code in on a non-raid bios. I don't know. If you were able to install in ahci mode, then that means it's working.

> Anyways, I'll try going back to IDE mode and see what happens. Got a bad feeling though.
Try it. Alternately, use AHCI on the JMicron. Those things work pretty well in ahci mode.

Just got home from work. Time for dinner. Be back a bit later...

---

### Post by maniacmusician on 2007-03-01
> **futz said:**
> Actually, there are pins at least. There may not be a jumper on em tho. :mrgreen: All SATA2 drives are backward compatible with SATA1 if you jumper the right two pins.
Right, that's what I meant :) I'm not **that** dumb, it's just my first build :). Of course there's pins, but yeah, no jumper on them.

> **futz said:**
> AHCI-disabled switches to IDE emu mode. The difference between Legacy IDE and Native IDE I don't know, but it sounds like Legacy is the safe setting and Native is the better setting if it works. I could be wrong. Legacy is default.
Yeah. 


> **futz said:**
> Oh ya! Big duh from me. Now I remember.


The bios won't show the drive in the IDE list if you are in AHCI mode. And that second page I was talking about may not even show on a non-raid bios. They may not have even put that piece of code in on a non-raid bios. I don't know. If you were able to install in ahci mode, then that means it's working.
No, it's not working...I was able to install, but only on the IDE drive. I couldn't see the SATA drive from the installation environment. I understand that it won't show up in the IDE list when in AHCI mode, but where would it show up? And the problem for me was, that even the installation disk could not see the SATA drive.


> **futz said:**
> Try it. Alternately, use AHCI on the JMicron. Those things work pretty well in ahci mode.

Just got home from work. Time for dinner. Be back a bit later...

Try what?

And how can I use AHCI on the JMicron? isn't that the IDE controller? 

Anyways, I got it to boot into a GUI. Funny thing; it still shows "Signal Out of Range" when the USplash is supposed to be displayed, but at least now it re-establishes itself when KDM shows up. I'm going to install nvidia drivers and stuff now. Let me know when you get any insights about how to get my SATA working properly.

This is my plan for the future; I'm going to get rid of the IDE junker. It's preventing me from using my second, faster optical drive right now, and I can't have that :) I'm going to take that hard drive out, and then buy another SATA hard drive. So it's really imperative that I get SATA working at full speed so I can enjoy the fruits of new system :) Although if we could somehow improve the speeds of the IDE (PATA) optical drives, I wouldn't be averse to that, either :)

Enjoy your dinner! :D sorry to be taking up so much of your time, though. You're just the person in the best position to help because of the hardware setup that you have...same processor, similar mobo, etc.

---

### Post by thecrumb on 2007-03-01
Got the same board and am having problems getting to to install... :(

Trying to install off the 6.06 Live CD (CD is good because I installed it on my other PC)

I can see the SATA drive in the bios during boot so I assume it's OK.

It starts and eventually hangs on "#bin/sh can't access TTY; Job control turned off"

So far digging on the forums hasn't turned up any solution... (lots of people with the same issue)

Jim

---

### Post by futz on 2007-03-01
> **maniacmusician said:**
> Right, that's what I meant :) I'm not **that** dumb, it's just my first build :). Of course there's pins, but yeah, no jumper on them.
Hehehehe!! LOL So much confusion. It's tough when you don't have the d@mn thing in front of you.

> No, it's not working...I was able to install, but only on the IDE drive. I couldn't see the SATA drive from the installation environment.
Ooooohhhh. Now I understand. 

> I understand that it won't show up in the IDE list when in AHCI mode, but where would it show up? And the problem for me was, that even the installation disk could not see the SATA drive.
On my board it shows up on that second AHCI BIOS screen. There's a chance that, even tho there's a bios setting for it, the ICH8 doesn't do ahci. I've read both that it doesn't, and in another post, that it does. Still reading...

If it turns out that it doesn't then you'll have to use the JMicron controller for your sata2 drives, or live with the slightly lower performance of non-ahci mode.

> Try what?
Try it in IDE emu mode. You already did by the time you read that anyway.

> And how can I use AHCI on the JMicron? isn't that the IDE controller?
Yes. It also controls the two purple sata connectors beside the four yellow ones that the ICH8 controls. If ahci is going to be a bear to get working on ICH8, then the JMicron should get ya going.

> Anyways, I got it to boot into a GUI. Funny thing; it still shows "Signal Out of Range" when the USplash is supposed to be displayed, but at least now it re-establishes itself when KDM shows up.
I've had that before. Change the resolution option in the grub bootup line. It's a command something like vga=791 at the end of the kernel line that boots linux. The number tells it what res to boot up in until X takes over.

---

### Post by maniacmusician on 2007-03-01
soooo....what's the next step? or are you still trying to figure that out?

---

### Post by futz on 2007-03-01
Yes, it's official. The ICH8 **does not** do AHCI. The ICH8R **does**. The option in the bios for it must be a mistake. They were probably cutting and pasting from the DQ6 code.

So plug your sata2 devices into the JMicron. Two 500GB drives should be adequate... Or a couple of those new terabyte drives... For now, anyway. :mrgreen: And you can plug four more drives into the ICH8 later. They just will work a tiny bit slower. Barely noticeable.

---

### Post by maniacmusician on 2007-03-01
I see. That's a bit of a bummer, but I can live with it.

So should I have AHCI and Native Mode enabled or not?

---

### Post by futz on 2007-03-01
> **maniacmusician said:**
> I see. That's a bit of a bummer, but I can live with it.
Ya, but not too big a deal. I forgot all about that detail when we first started this thread. Guess I shoulda remembered and up-sold ya to a DQ6, huh?

> So should I have AHCI and Native Mode enabled or not?
AHCI disabled (that enables IDE emulation mode).

Here's some info on legacy (compatible) & native ide modes:

[http://www.microsoft.com/whdc/device/storage/Native-modeATA.mspx](http://www.microsoft.com/whdc/device/storage/Native-modeATA.mspx)

Compatible mode. A controller that operates in compatible mode emulates a legacy IDE controller, which is a non-standard extension of the ISA-based IDE controller. In compatible mode, the controller requires two ISA-style dedicated IRQs (14 and 15) that cannot be shared with other devices. Because compatible mode requires dedicated resources, the ATA controller for the boot device (which is usually integrated in chipsets on the motherboard) is the only controller on a system that is likely to operate in compatible mode.

Native mode. A controller that operates in native mode acts as a true PCI device that does not require dedicated legacy resources and can be configured anywhere in the system. ATA controllers running in native mode use their PCI interrupt for both channels and can share this interrupt with other devices in the system, like any other PCI device. Add-in ATA controllers generally operate in native mode.

Try native, but if it doesn't work, go with the default legacy. It's just a matter of how it deals with IRQ's. In native mode they're steerable. In compatible mode they're locked to 14 & 15 and not steerable.

---

### Post by maniacmusician on 2007-03-01
I see. Thanks, I'll try that when I have enough money to order another SATA drive.


On another note, related to this system, how can I make sure that my dual-core capabilities are being used? I mean, it feels fast enough so that I'm sure they are, but that could just be the increase in L2 cache from my last comp. How can I make sure?

How can I make sure that my RAM is using the dual-channel feature of the motherboard?

Is there anything that I have to/should do to take better advantage of the new system? Haven't worked with dual-cores on Linux yet, so I'm not sure.

update: I just installed some official nvidia drivers on the box, and they give me the "signal out of range" thing on the monitor as well. This is fishy,

---

### Post by futz on 2007-03-01
> **maniacmusician said:**
> On another note, related to this system, how can I make sure that my dual-core capabilities are being used? I mean, it feels fast enough so that I'm sure they are, but that could just be the increase in L2 cache from my last comp. How can I make sure?
You used to have to install the SMP (Symmetrical Multi Processing) version of the kernel. Since a couple kernels ago, though, you just use the Generic version of the kernel, which has SMP built in. It detects your multi-core cpu automagically. To check if it's actually using both, start System Monitor and look at the Resources tab. if there's two cpu's listed there, you're good.

> How can I make sure that my RAM is using the dual-channel feature of the motherboard?
Just make sure the two sticks are plugged into (on Gigabyte boards) same-color slots. Channel-0 is the first two slots and Channel-1 is the second two. You want one stick in each channel. Watch when you boot up. The first screen should say your memory is being accessed as dual channel interleaved, or somesuch phrase.

> Is there anything that I have to/should do to take better advantage of the new system? Haven't worked with dual-cores on Linux yet, so I'm not sure.
Not that I can think of off-hand. Just have fun.

> update: I just installed some official nvidia drivers on the box, and they give me the "signal out of range" thing on the monitor as well. This is fishy,
Back when I had that problem, I was using one of the beta versions and they just hadn't fixed up the splash screen yet. Once they fixed it the problem went away. You installed Edgy? That shouldn't have any problem. Ya might wanna search the forum for other people having that problem, cuz I don't know what's up.

---

### Post by maniacmusician on 2007-03-02
okay, thanks. I'm going to do a reinstall with Feisty when I get my new hard drive anyways. I hope it's not a hardware problem because of me hooking up something the wrong way. 

RAM: yeah, I did stick it in the same-colored slots. I'll look for that phrase at boot.

2 CPU's: I don't have Gnome. Gotta find a way to check in KDE.....

---

### Post by futz on 2007-03-02
> **maniacmusician said:**
>  I don't have Gnome. Gotta find a way to check in KDE.....
ksysguard?

I don't know. I don't really like kde.

---

### Post by maniacmusician on 2007-03-02
:) it's fine.



I just thought of something though. There's probably a newer BIOS out for my system. How would I go about upgrading it? perhaps that'll help sort some of this madness.

---

### Post by futz on 2007-03-02
> **maniacmusician said:**
> :) There's probably a newer BIOS out for my system. How would I go about upgrading it? perhaps that'll help sort some of this madness.
Don't do it in windows!!! Hehehe! A bunch of Asus users recently found that out the hard way. There was some kind of bug in the windows flasher. They all ended up sending their boards back to be reflashed.

The flasher is built into the BIOS. It's called Q-Flash or somesuch. Easy as pie to use. Refer to your manual. I think you hit Del to go to BIOS, then hit F8 to go to BIOS management (you have multi-bios on that board) and there's an option to flash it. Before you do all that, tho, you should have downloaded the latest bios image and have it on a floppy, ready to go. Be sure you have the correct one, but if you don't it's not the end of the world, since you have a backup bios that will take over if the new one won't post.

---

### Post by maniacmusician on 2007-03-02
Damn...I don't have a floppy drive. Those things are generally useless and I've thrown mine out a long time ago.

Any other way? :)

---

### Post by futz on 2007-03-02
> **maniacmusician said:**
> Damn...I don't have a floppy drive. Those things are generally useless and I've thrown mine out a long time ago.

Any other way? :)
Not that I know of. Buy one. Here they're about $11. Peanuts. Or steal one from a junker box. They never wear out cuz nobody uses em.

---

### Post by maniacmusician on 2007-03-02
True, I guess I could scavenge one from an older box. don't really want to...it just sounds like a pain in the ***. 

But I guess I'll have to get around to it. Thanks for all your help. Hopefully, this will all turn out well in the end.

PS: My idle CPU temp seems to be around 30-32 degrees. Seems a little high? I haven't overclocked or anything like that yet, so I think the idle should be in the 20s. I did use Arctic Silver instead of the stock paste, so I think i should be seeing some results. Yeah, yeah, they did say 200 hours and a certain amount of cycles. But still. Other people have reported similar idle temps when OC'dl.

---

### Post by futz on 2007-03-02
> **maniacmusician said:**
> True, I guess I could scavenge one from an older box. don't really want to...it just sounds like a pain in the ***.
Easy! Nothin to it. If you only need it for just the one flash, just hang it out the side till done. Then unplug and toss in a drawer for next time.

> My idle CPU temp seems to be around 30-32 degrees. Seems a little high?
That's just fine. I wouldn't be the least bit concerned. Those guys with lower idle temps are probably running big aftermarket coolers. Also there is some variation in parts. Some cpu's just naturally run cooler or warmer than others. Nothing to be concerned about.

---

### Post by maniacmusician on 2007-03-02
The person I was actually talking about was Anthony Haslam, a guy on the forums here who I helped put together a similar system a while back. He's running an E6300 OC'd to 2.5GHz and its running idle at 30; with stock cooling.

But you're right, I don't really have to worry about it right now, as I won't be tackling OC'ing for a few months.

---

### Post by thecrumb on 2007-03-02
So I'm re-reading all these threads this AM and the consensus is:

- use the JMicron SATA plugs (the 2 purple ones) vs. the (4) ICH8 ones?
- disable AHCI
- set the SATA mode to IDE compatible (not native)

I downloaded 6.10 last night but was too tired to continue... will try again tonight when I get home.  

Jim

---

### Post by maniacmusician on 2007-03-02
> **thecrumb said:**
> So I'm re-reading all these threads this AM and the consensus is:

- use the JMicron SATA plugs (the 2 purple ones) vs. the (4) ICH8 ones?
- disable AHCI
- set the SATA mode to IDE compatible (not native)

I downloaded 6.10 last night but was too tired to continue... will try again tonight when I get home.  

Jim
the mode doesn't have to be Legacy IDE; I'm going to try Native, as it will give me better performance, supposedly.

As for the JMicron thing, yeah; you should use the two purple ones if you want the full benefits of SATA, according to futz. 

I have a question though, and maybe someone can answer it...If the JMicron is capable of AHCI, then why should I disable it in the BIOS? Is AHCI for the JMicron enabled by default? What's the deal with that?

---

### Post by thecrumb on 2007-03-02
**Update:**

Last night I downloaded a burned a **6.10** iso but was too tired to try it...

This afternoon I got home - threw in the CD - booted and then got sidetracked playing with my kids.  About an hour later I check on the PC and it's at the* Live CD desktop*!

This was using:
 Native mode: disabled
 Sata/IDE mode: IDE

So I wondered if I switched these if it would boot...

I switched to:
 Native mode: Enabled
 Sata/IDE mode: AHCP

Rebooted and the pc hung with a message:

 HDA: ide_intr: huh? expected null handler on exit... and there was something about HDA...

This kept repeating and I got impatient and then tried a few more variations - all with the same results...  the 'huh' error and me rebooting...

Finally I reset the mobo with the failsafe options - rebooted and once again left it for a bit.

When I came back - again it was at the Live CD desktop!

This time I popped open a terminal and did a 'sudo fdisk -l' and it had my SATA drive listed as SDA! Woot!

So now I went back - reset it again to:
 Native mode: enabled
 Sata/IDE mode: AHCP

Rebooted - waited FOREVER and again - the Live CD popped up.  I checked and again SDA was available.  So now I continued with the install and right now it's formatting the HD... 

I'll update again if that's successful...

Right now I just selected to erase everything and let Ubuntu partition it as it likes but is that the best way to go??  Anyone have a good partition FAQ/guide?

Thanks,
Jim

---

### Post by maniacmusician on 2007-03-02
The best way to go is to make a seperate partition for /home (or for /home/username). Then, you edit the mountpoint of the drive to be /home or /home/username/ and that way, your data is protected during reinstalls. it's pretty cool.


So where is this SATA/IDE mode that you're talking about? I don't think that's the name of the option, is it? could you give more specific details?

---

### Post by thecrumb on 2007-03-02
Update: 

It seems to have installed OK  Boots up fine but no network.

Off to dig through the forums to see if I can find the solution to that issue...

Jim

---

### Post by thecrumb on 2007-03-02
*So where is this SATA/IDE mode that you're talking about? I don't think that's the name of the option, is it? could you give more specific details?*

On the **Integrated Peripherals** menu:

SATA Port0-3 Native Mode:  Enabled
Onboard SATA/IDE Device: Enabled
Onboard SATA/IDE Ctrl Mode: AHCI    (sorry - my previous posts said AHC*P*)

Doing a quick search on the net - onboard LAN seems to be a problem as well so i just dropped in a 3Com NIC I had out of an older PC and disabled the on-board in the BIOS.

Next - need to get my resolution fixed and migrate everything over from my old PC.

I'll look at making a /home mount... that does seem handy!

Jim

---

### Post by maniacmusician on 2007-03-02
Would you mind telling me what you had for "SATA AHCI Mode" ? It should be the first option in the Integrated Peripherals menu.

and yeah, /home mounts are awesome for multiple user systems. /home/username is more suited to single-user systems. But yeah, either way, they're both a step up from the normal method.

---

### Post by thecrumb on 2007-03-02
Hmm - the first option in my Integrated Peripherals menu is:

SATA Port0-3 Native Mode  (which I have Enabled)

The manual states:

Disabled - set port to operate at Legacy IDE mode (default)
Enabled - set port to operate at Native IDE mode.

Jim

---

### Post by maniacmusician on 2007-03-02
I see. It's kind of weird that you don't have that option...[shrug]. Oh well.

---

### Post by thecrumb on 2007-03-02
Maybe different BIOS versions?

On the box my mobo came in it says:

GA-965P-DS3 rev3.3

Jim

---

### Post by maniacmusician on 2007-03-02
> **thecrumb said:**
> Maybe different BIOS versions?

On the box my mobo came in it says:

GA-965P-DS3 rev3.3

Jim
same here

---

### Post by flyingbrass on 2007-03-03
You can see your BIOS version and other info with:

sudo dmidecode | less

Good luck.  I hope any lingering Jmicron issues get fixed before Feisty's release.

---

### Post by thecrumb on 2007-03-03
Another quick followup - this AM I discovered I had a 80GB SATA drive in my old PC so I moved it to the new one - think I'm going to use this to do sync backups...

Just a note - I know there was discussion before about using the purple SATA connectors (JMicron?) and not the yellow ones but my two drives ARE plugged into the yellow slots (0 & 1)

Jim

---

### Post by maniacmusician on 2007-03-03
> **flyingbrass said:**
> You can see your BIOS version and other info with:

sudo dmidecode | less

Good luck.  I hope any lingering Jmicron issues get fixed before Feisty's release.
Thanks for the command, it's handy. 

Oh, and all JMicron issues are fixed. They were fixed even for Edgy, I think. The problem I was having had nothing to do with JMicron,  but rather the fact that my chipset did not support AHCI. That's all.


> **thecrumb said:**
> Another quick followup - this AM I discovered I had a 80GB SATA drive in my old PC so I moved it to the new one - think I'm going to use this to do sync backups...

Just a note - I know there was discussion before about using the purple SATA connectors (JMicron?) and not the yellow ones but my two drives ARE plugged into the yellow slots (0 & 1)

Jim

Cool; spare hard drives are great. So umm how are your speeds with the two drives in the yellow slots? If they both run at the same speed (probably 7200 RPM), test it by transferring a large file from one drive to the other. I want to know if AHCI is really working and if you're getting the true speed of SATAII.

Also, do your devices show up as  SCSI devices (sda/sdb), or normal HDD devices (hda/hdb)?

---

### Post by thecrumb on 2007-03-04
> **maniacmusician said:**
> Cool; spare hard drives are great. So umm how are your speeds with the two drives in the yellow slots? If they both run at the same speed (probably 7200 RPM), test it by transferring a large file from one drive to the other. I want to know if AHCI is really working and if you're getting the true speed of SATAII.

Also, do your devices show up as  SCSI devices (sda/sdb), or normal HDD devices (hda/hdb)?


They *seem* fast - I can move the 6.10 ISO between disks in a few seconds (6-10)

Is there any way to accurately measure the throughput??

What I may do now that everything is working is to switch the drives over to the other controller (purple) to see if it will boot and if there is any difference in speed.  I may also change the bios settings to see if that changes anything.

Drives are listed as:   sda1 sdb1

Jim

---

### Post by maniacmusician on 2007-03-04
cool, let me know how that goes :)

---

### Post by aidanr on 2007-03-24
so does anyone have any recommendations for a board that has similar specs but doesn't have all these problems and everthing just works?

i'm picking parts for a very similar rig at the moment, and was looking at the dq6 untill i saw this thread :|

---

### Post by maniacmusician on 2007-03-24
> **aidanr said:**
> so does anyone have any recommendations for a board that has similar specs but doesn't have all these problems and everthing just works?

i'm picking parts for a very similar rig at the moment, and was looking at the dq6 untill i saw this thread :|
I'd go for it. I'm not having any problems with my board, the settings were just a little confusing and it took a little bit of tweaking to get it to recognize the hard drives. After that, it's been smooth sailing.

---

