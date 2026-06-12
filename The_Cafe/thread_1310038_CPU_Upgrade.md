---
title: "CPU Upgrade"
date: 2009-11-01
forum: The Cafe
---

### Post by lovinglinux on 2009-11-01
I'm planning to upgrade my CPU. Do I need to reset the BIOS and do something on Ubuntu or is a CPU pretty much plug-and-play?

Additionally what do you think about Core 2 Duo E7400 2.8GHz e 3Mb?

I currently have a P4 3.06 Ghz HT with 2 GB DDR2 RAM, Gigabyte GA-945GCM-S2C mobo and nvidia 7300GT. Will be a huge difference in performance with Core 2 Duo?

---

### Post by ZankerH on 2009-11-01
I made a similar move from a pentium 4 to an intel C2D E6700 last year. It worked without doing anything to ubuntu or BIOS, and the performance improvement was very much worth it.

---

### Post by Zoot7 on 2009-11-01
> **lovinglinux said:**
> I'm planning to upgrade my CPU. Do I need to reset the BIOS and do something on Ubuntu or is a CPU pretty much plug-and-play?
You won't have to do anything; I cloned the hard drive out of my laptop which is using the Core 2 Duo T7500 and put it into my homebuilt desktop - the Phenom II X4 955 worked fine upon booting up. Also once the BIOS recognises the new CPU you're away.

> **lovinglinux said:**
> Additionally what do you think about Core 2 Duo E7400 2.8GHz e 3Mb?

I currently have a P4 3.06 Ghz HT with 2 GB DDR2 RAM, Gigabyte GA-945GCM-S2C mobo and nvidia 7300GT. Will be a huge difference in performance with Core 2 Duo?
That's a good choice of CPU, you might have to update your BIOS to the latest version to the get the motherboard to recognize it and use it properly mind you.
For lots of multitasking in Ubuntu I'd say you'll notice a considerable difference but otherwise not much.

EDIT: According to this you'll have to use BIOS F6a to get the E7400 up and running.
[http://www.gigabyte.com.tw/Support/Motherboard/CPUSupport_Model.aspx?ProductID=2668#anchor_os](http://www.gigabyte.com.tw/Support/Motherboard/CPUSupport_Model.aspx?ProductID=2668#anchor_os)

---

### Post by Skripka on 2009-11-01
> **lovinglinux said:**
> I'm planning to upgrade my CPU. Do I need to reset the BIOS and do something on Ubuntu or is a CPU pretty much plug-and-play?

Additionally what do you think about Core 2 Duo E7400 2.8GHz e 3Mb?

I currently have a P4 3.06 Ghz HT with 2 GB DDR2 RAM, Gigabyte GA-945GCM-S2C mobo and nvidia 7300GT. Will be a huge difference in performance with Core 2 Duo?

You'll see a bump in preformance.  But it depends on what you are doing now, in terms of multitasking etc.  Your mainboard only supports up to DDR2-667 memory--so there's a chance that could be where your bottleneck is....and if your memory is not the bottleneck currently, it will become it post CPU upgrade.

---

### Post by lovinglinux on 2009-11-01
> **Zoot7 said:**
> You won't have to do anything; I cloned the hard drive out of my laptop which is using the Core 2 Duo T7500 and put it into my homebuilt desktop - the Phenom II X4 955 worked fine upon booting up. Also once the BIOS recognises the new CPU you're away.

Thank you. That's great.

> **Zoot7 said:**
> That's a good choice of CPU, you might have to update your BIOS to the latest version to the get the motherboard to recognize it and use it properly mind you.

EDIT: According to this you'll have to use BIOS F6a to get the E7400 up and running.
[http://www.gigabyte.com.tw/Support/Motherboard/CPUSupport_Model.aspx?ProductID=2668#anchor_os](http://www.gigabyte.com.tw/Support/Motherboard/CPUSupport_Model.aspx?ProductID=2668#anchor_os)

I have to check the BIOS version. The mobo box says it supports Core 2 Duo, but I guess must be an older model.

> **Zoot7 said:**
> For lots of multitasking in Ubuntu I'd say you'll notice a considerable difference but otherwise not much.

The P4 performance is good. It just suffers when for example rkhunter is scanning the system or when I'm using sed on a file with more than a million lines. Then the CPU usage goes to the roof and other applications become laggy.

> **Skripka said:**
> You'll see a bump in preformance.  But it depends on what you are doing now, in terms of multitasking etc.  Your mainboard only supports up to DDR2-667 memory--so there's a chance that could be where your bottleneck is....and if your memory is not the bottleneck currently, it will become it post CPU upgrade.

Hmm, that's interesting. I'm having second thoughts already. Perhaps I should spend the money on new monitor instead :) I can't replace the mobo, memory and CPU, right now. So, if the memory will become the bottleneck, then is not worthy, is it?

---

### Post by Skripka on 2009-11-01
> **lovinglinux said:**
> 


Hmm, that's interesting. I'm having second thoughts already. Perhaps I should spend the money on new monitor instead :) I can't replace the mobo, memory and CPU, right now. So, if the memory will become the bottleneck, then is not worthy, is it?

There will always be a bottle neck.  The question is what it is, and when it comes into play.  LGA775 hardware is cheap now, as is DDR2--because it is obsolete by i7/i5 standards.

---

### Post by schmidtbag on 2009-11-01
i would recommend amd for now.  they're cheaper and unless you're looking for a supercomputer, they're just as good as the intel competitor chip  for a significantly lower price.  if you want some raw power, go for intel's i7 but only go for their newer models which are blazing fast, the early ones aren't very good.  the i5 is pretty terrible, amd's phenom II triple core can often outperform it.  so, if this is just a standard computer, nothing too special, go for amd's athlon II.  if you want a high-end computer, go for i7.  if you want a middle-high, go for phenom II.  whether amd's competitive chips are a little slower, the price is so worth it

---

### Post by NoaHall on 2009-11-01
> **schmidtbag said:**
> i would recommend amd for now.  they're cheaper and unless you're looking for a supercomputer, they're just as good as the intel competitor chip  for a significantly lower price.  if you want some raw power, go for intel's i7 but only go for their newer models which are blazing fast, the early ones aren't very good.  the i5 is pretty terrible, amd's phenom II triple core can often outperform it.  so, if this is just a standard computer, nothing too special, go for amd's athlon II.  if you want a high-end computer, go for i7.  if you want a middle-high, go for phenom II.  whether amd's competitive chips are a little slower, the price is so worth it

Ehm. He wants to upgrade and keep the same everything else. To do what you say, he'll need a new motherboard.

---

### Post by lovinglinux on 2009-11-01
> **NoaHall said:**
> Ehm. He wants to upgrade and keep the same everything else. To do what you say, he'll need a new motherboard.

Yep, I can't afford a full upgrade right now. Besides I have already replaced the motherboard and memory about a year ago, after my ASUS mobo melted down. So the hardware is not very old.

---

### Post by Zoot7 on 2009-11-01
> **lovinglinux said:**
> So, if the memory will become the bottleneck, then is not worthy, is it?
Most benchmarks point to pretty much no advantage in DDR2-800 over DDR2-667. Same goes with DD2 v DDR3.

The biggest bottleneck normally is the bus link between the CPU and the Northbridge, normally your memory is able to talk to your Northbridge faster than your CPU is able to, so faster memory is normally much of a muchness.

---

### Post by lovinglinux on 2009-11-01
> **Zoot7 said:**
> Most benchmarks point to pretty much no advantage in DDR2-800 over DDR2-667. Same goes with DD2 v DDR3.

The biggest bottleneck normally is the bus link between the CPU and the Northbridge, normally your memory is able to talk to your Northbridge faster than your CPU is able to, so faster memory is normally much of a muchness.

So, do you think it will be a bottleneck?

---

### Post by NoaHall on 2009-11-01
> **lovinglinux said:**
> So, do you think it will be a bottleneck?

2GB? Nah.

---

### Post by Zoot7 on 2009-11-01
> **lovinglinux said:**
> So, do you think it will be a bottleneck?
Nope. :)

---

### Post by tom66 on 2009-11-01
Hey, I'm probably going to do a similar thing with a Celeron D 346 3.06GHz. The chip runs very cool (30 C), despite having a TDP of 85W. I'm thinking of changing it to a Core 2 Duo 2.66 GHz (for about $50), which has a lower TDP of 65W, and should cope better with Full HD video, as I might be adding HD output to my PC soon. I will also be adding an nVidia 7300 LE video card, so I'll see if this lets me offload to hardware for some decoding, or if I'll need a new processor as well.

Few questions, to everyone else:
[list]
[*]The current processor runs at 1.38 volts - but the Core 2 runs at 1.25 volts. So will the motherboard automatically adjust the voltage, or will I have to do it some other way?
[*]At a clock rate of 3.06 GHz, it has a multiplier of 22.0x. Do I need to change this, or will it change itself?
[*]At the moment, there is a huge, passive heatsink on the chip, and there are two adjacent fans to the processor to improve air flow over the heatsink. It runs very quiet and also very cool. Will I be able to use this heatsink with the newer chip, or can you only use a heatsink once?
[/list]

---

### Post by Zoot7 on 2009-11-01
> **tom66 said:**
> [list]
[*]The current processor runs at 1.38 volts - but the Core 2 runs at 1.25 volts. So will the motherboard automatically adjust the voltage, or will I have to do it some other way?
[*]At a clock rate of 3.06 GHz, it has a multiplier of 22.0x. Do I need to change this, or will it change itself?
[*]At the moment, there is a huge, passive heatsink on the chip, and there are two adjacent fans to the processor to improve air flow over the heatsink. It runs very quiet and also very cool. Will I be able to use this heatsink with the newer chip, or can you only use a heatsink once?
[/list]
1 - The Motherboard will automatically adjust the voltage, you shouldn't have to do anything.
2 - Nope, it'll change itself.
3 - Yes you can, just be sure to clean it off and re-apply a new bit of thermal paste.

---

### Post by Skripka on 2009-11-01
> **tom66 said:**
> Hey, I'm probably going to do a similar thing with a Celeron D 346 3.06GHz. The chip runs very cool (30 C), despite having a TDP of 85W. I'm thinking of changing it to a Core 2 Duo 2.66 GHz (for about $50), which has a lower TDP of 65W, and should cope better with Full HD video, as I might be adding HD output to my PC soon. I will also be adding an nVidia 7300 LE video card, so I'll see if this lets me offload to hardware for some decoding, or if I'll need a new processor as well.

Few questions, to everyone else:
[list]
[*]The current processor runs at 1.38 volts - but the Core 2 runs at 1.25 volts. So will the motherboard automatically adjust the voltage, or will I have to do it some other way?
[*]At a clock rate of 3.06 GHz, it has a multiplier of 22.0x. Do I need to change this, or will it change itself?
[*]At the moment, there is a huge, passive heatsink on the chip, and there are two adjacent fans to the processor to improve air flow over the heatsink. It runs very quiet and also very cool. Will I be able to use this heatsink with the newer chip, or can you only use a heatsink once?
[/list]

1 & 2)  The BIOS will automatically detect the differences in voltage and multiplier, and set it accordingly per defaults.

3)  The new CPU will come with a HSF, and pre-applied thermal compound.  If you're thinking about OC-ing, ditch the crap stock thermal compound for Arctic Silver 5.  Heatsinks can be reused-but the one that would come with the new Core2 CPU will be better as it is not a passive unit.

---

### Post by lovinglinux on 2009-11-01
> **tom66 said:**
> I'm thinking of changing it to a Core 2 Duo 2.66 GHz (for about $50)

WOW, 50 bucks? that's cheap. Here it costs 5 x more. The one I want costs R$ 480,00 = U$275,00.

---

### Post by Skripka on 2009-11-01
> **lovinglinux said:**
> WOW, 50 bucks? that's cheep. Here it costs 5 x more. The one I want costs R$ 480,00 = U$275,00.

Wowza, I dunno where you're shopping-but it sounds like you're being wallet-raped.  $300USD gets you a Core i7 quad CPU here in the US.

---

### Post by lovinglinux on 2009-11-01
> **Skripka said:**
> Wowza, I dunno where you're shopping-but it sounds like you're being wallet-raped.  $300USD gets you a Core i7 quad CPU here in the US.

Well, I live in Brazil my friend ;)

---

### Post by tom66 on 2009-11-02
> **Skripka said:**
> 1 & 2)  The BIOS will automatically detect the differences in voltage and multiplier, and set it accordingly per defaults.

3)  The new CPU will come with a HSF, and pre-applied thermal compound.  If you're thinking about OC-ing, ditch the crap stock thermal compound for Arctic Silver 5.  Heatsinks can be reused-but the one that would come with the new Core2 CPU will be better as it is not a passive unit.

I won't be overclocking, I'm just using it as a media PC. I'll probably be OK using the stock thermal paste. 

The heatsink is a very large copper heatsink, with several heatpipes. I don't know the thermal resistance, but I'd expect it is pretty good and up to spec. I'll consider using some special thermal paste, to make sure I don't fry my new chip.

Also, how do I know my chip is compatible? I've got a LGA775 socket, but I don't if the chipset is compatible... How do I tell?

---

### Post by PurposeOfReason on 2009-11-02
> **lovinglinux said:**
> Well, I live in Brazil my friend ;)
Shipping? If not I would gladly buy you parts and ship them if it was cheaper.

---

### Post by Zoot7 on 2009-11-02
> **lovinglinux said:**
> The one I want costs R$ 480,00 = U$275,00.
Ouch!

> **tom66 said:**
> Also, how do I know my chip is compatible? I've got a LGA775 socket, but I don't if the chipset is compatible... How do I tell?
What kind of motherboard have you? The best thing to do is look up the CPU support list from the motherboard manafacturer's website; that'll tell you whether or not the motherboard supports it and also whether or not you need to upgrade the BIOS to get it to work.

---

### Post by BuffaloX on 2009-11-02
Funny it's only a couple of weeks, since one of my friends asked a similar question.
He wanted the 2.8 Ghz Core2 duo at about 900,- DKR. (about 180,- USD)
Doing a quick search on the Internet, I found he could get a similar CPU, just 2.5 GHZ for only 350,- DKR. (about 70,- USD).

Sometimes only 10% speed increase doubles the price, buying at the "sweet spot" and from a competitive supplier, can save you a lot of money.

Any Core2 will be faster than your P4 CPU, the P4 is infamous for its long pipeline, which stalls much too easily resulting in lots and lots of lost cycles.

If this is your first time installing a CPU, you should read a guide on applying thermal paste.
Correctly applied thermal paste is much more important than using higher quality paste.

---

### Post by tom66 on 2009-11-02
> **Zoot7 said:**
> Ouch!


What kind of motherboard have you? The best thing to do is look up the CPU support list from the motherboard manafacturer's website; that'll tell you whether or not the motherboard supports it and also whether or not you need to upgrade the BIOS to get it to work.
Unfortunately it seems to be a custom motherboard for my media PC. For example it has no serial/parallel ports, no keyboard/mouse, and 7.1 surround sound RCA jacks...

I just checked the chipset. Unfortunately it's not Core 2 compatible, or even Core compatible. Only Celerons and Pentiums. I'll see about upgrading to a Pentium...

---

### Post by Regenweald on 2009-11-02
> **lovinglinux said:**
> Well, I live in Brazil my friend ;)

I live in the caribbean and use a skybox. I come out **way** cheaper, else I'd have to buy the most cutting edge processors the local retailers supply: an AthlonX2 6000 at 700$TT roughly 120USD

> **PurposeOfReason said:**
> Shipping? If not I would gladly buy you parts and ship them if it was cheaper.

I'd take him up on this. Brazil seems forward thinking when it comes to tech and if you're lucky like me, they don't charge duties on computer parts here.

---

### Post by lovinglinux on 2009-11-02
> **PurposeOfReason said:**
> Shipping? If not I would gladly buy you parts and ship them if it was cheaper.

Thank you very much, but I'm afraid shipping and import taxes would be a deal breaker.

> **BuffaloX said:**
> Funny it's only a couple of weeks, since one of my friends asked a similar question.
He wanted the 2.8 Ghz Core2 duo at about 900,- DKR. (about 180,- USD)
Doing a quick search on the Internet, I found he could get a similar CPU, just 2.5 GHZ for only 350,- DKR. (about 70,- USD).

Sometimes only 10% speed increase doubles the price, buying at the "sweet spot" and from a competitive supplier, can save you a lot of money.


These are the CPU models I'm interested now. 

Pentium Dual-Core E5200(2.50GHz,2MB) - 800 MHz FSB - U$ 153.00  (trusted shop)
Pentium Dual-Core E5300(2.60GHz,2MB) - 800 Mhz FSB - U$ 170.00 (trusted shop)

Core&#8482; 2 Duo E4600(2.40GHz,2MB) 800 MHz FSB - U$ ???
Core&#8482; 2 Duo E4700(2.60GHz,2MB) 800 MHz FSB - U$ ??? (discontinued)

Core&#8482; 2 Duo E7300(2.66GHz,3MB) 1066 MHz FSB - U$ ???
Core&#8482; 2 Duo E7400(2.8GHz,3MB) 1066 MHz FSB - U$ 275.00  (trusted shop)
Core&#8482; 2 Duo E7500(2.93GHz,3MB) 1066 MHz FSB  - U$ 210.00


> **BuffaloX said:**
> If this is your first time installing a CPU, you should read a guide on applying thermal paste.Correctly applied thermal paste is much more important than using higher quality paste.

Thanks. I know how to do that, I just never installed a new CPU model.

---

### Post by lovinglinux on 2009-11-02
> **Regenweald said:**
> I'd take him up on this. Brazil seems forward thinking when it comes to tech and if you're lucky like me, they don't charge duties on computer parts here.

Last time I checked, the import tax here for computer parts was around 60%.

---

### Post by PurposeOfReason on 2009-11-02
> **lovinglinux said:**
> Thank you very much, but I'm afraid shipping and import taxes would be a deal breaker.




These are the CPU models I'm interested now. 

Pentium Dual-Core E5200(2.50GHz,2MB) - 800 MHz FSB - U$ 153.00  (trusted shop)
Pentium Dual-Core E5300(2.60GHz,2MB) - 800 Mhz FSB - U$ 170.00 (trusted shop)

Core™ 2 Duo E4600(2.40GHz,2MB) 800 MHz FSB - U$ ???
Core™ 2 Duo E4700(2.60GHz,2MB) 800 MHz FSB - U$ ??? (discontinued)

Core™ 2 Duo E7300(2.66GHz,3MB) 1066 MHz FSB - U$ ???
Core™ 2 Duo E7400(2.8GHz,3MB) 1066 MHz FSB - U$ 275.00  (trusted shop)
Core™ 2 Duo E7500(2.93GHz,3MB) 1066 MHz FSB  - U$ 210.00




Thanks. I know how to do that, I just never installed a new CPU model.
Get the 5200. It's an overclocking beast.

---

### Post by Zoot7 on 2009-11-02
> **tom66 said:**
> I just checked the chipset. Unfortunately it's not Core 2 compatible, or even Core compatible. Only Celerons and Pentiums. I'll see about upgrading to a Pentium...
That'll mean you're more than likely stuck to single cores only. What chipset does it have?

> **lovinglinux said:**
> Core™ 2 Duo E7300(2.66GHz,3MB) 1066 MHz FSB - U$ ???
Core™ 2 Duo E7400(2.8GHz,3MB) 1066 MHz FSB - U$ 275.00  (trusted shop)
Core™ 2 Duo E7500(2.93GHz,3MB) 1066 MHz FSB  - U$ 210.00
Personally, I'd go for any one of those. The faster the FSB the better, that's almost always the biggest bottleneck.

---

### Post by BuffaloX on 2009-11-02
> **lovinglinux said:**
> Last time I checked, the import tax here for computer parts was around 60%.

> **PurposeOfReason said:**
> Get the 5200. It's an overclocking beast.

With that kind of taxes, I'd really look into over-clocking.
I used to do it, using water-cooling.

Oh the memories, like the good old Celeron 300 Mhz which could overclock to 450 with a pure FSB overclock 66 -> 100 Mhz.
That made it faster than the fastest available Pentium at stock speed, partly due to its on dye cache, which when overclocked ran twice as fast as the Pentium.

Or the old 8 Mhz 286, put an icecap on it, and replace the main clock crystal with a 12 Mhz one, and you almost had a supercomputer. :p

---

### Post by NoaHall on 2009-11-02
> **PurposeOfReason said:**
> Get the 5200. It's an overclocking beast.

How much have you risen it to?

---

### Post by Frak on 2009-11-02
General rule for Windows, in case you have it:

You can go from Single Core to Multi Core, but NEVER go backwards. Windows removes the single-core ACPI & PAM HALs when a multi-core processor is detected. If you go back to single-core, it will bluescreen on boot (unless they fixed it).

Again, don't know if it applies to Ubuntu, but might as well inform you about it.

---

### Post by Zoot7 on 2009-11-02
> **BuffaloX said:**
> Oh the memories, like the good old Celeron 300 Mhz which could overclock to 450 with a pure FSB overclock 66 -> 100 Mhz.
That made it faster than the fastest available Pentium at stock speed, partly due to its on dye cache, which when overclocked ran twice as fast as the Pentium.

Or the old 8 Mhz 286, put an icecap on it, and replace the main clock crystal with a 12 Mhz one, and you almost had a supercomputer. :p
Oh the joys of overclocking... I used to run my old AMD Sempron 2600+ at 2.2GHz. The best overclock I've done was 4Ghz @ nearly 1.6V on the old Q9450 I had, knocked it back to 3.2GHz, ran it like that for a few months. Then I just got sick of it and dialed it back to stock and haven't overclocked since. I still haven't overclocked my Phenom II yet, unlocked multiplier and all'. :p

---

### Post by PurposeOfReason on 2009-11-02
> **NoaHall said:**
> How much have you risen it to?
I believe 3.8 was my daily driver but I got it to 4.6 with some water that made a quick super pi run.

---

### Post by NoaHall on 2009-11-03
> **PurposeOfReason said:**
> I believe 3.8 was my daily driver but I got it to 4.6 with some water that made a quick super pi run.

OH, niceee.

---

### Post by PurposeOfReason on 2009-11-03
> **NoaHall said:**
> OH, niceee.
Should add some notes.

1) Results not typical
2) Results from someone who really knows what he is doing/lots of time
3) Water, water, and more water. Oh, and ice cubes*.

*For the love of God, do no put ice in a WC loop unless you know what you are doing and have taken precautions.

---

### Post by NoaHall on 2009-11-03
> **PurposeOfReason said:**
> Should add some notes.

1) Results not typical
2) Results from someone who really knows what he is doing/lots of time
3) Water, water, and more water. Oh, and ice cubes*.

*For the love of God, do no put ice in a WC loop unless you know what you are doing and have taken precautions.

I know how to OC, thank you very much :)

---

### Post by PurposeOfReason on 2009-11-03
> **NoaHall said:**
> I know how to OC, thank you very much :)
Not saying you don't. I just don't want someone to come in, see that, buy a 5200 and then throw the FSB out the window thinking magic will happen. Well, there will be smoke and maybe a mirror in said room, but that's about it.

---

### Post by tom66 on 2009-11-06
> **Zoot7 said:**
> That'll mean you're more than likely stuck to single cores only. What chipset does it have?


Personally, I'd go for any one of those. The faster the FSB the better, that's almost always the biggest bottleneck.
It has an Intel 915P, I think. 

However, I did just test it with a 1080p video. Remarkably, it can in fact play it, at about 80-90% CPU usage. However, I wonder if it's not rendering so much because I'm on a PAL TV and stuck at 800x600 (scaled to 720x576)? Notably, VLC struggles (freezing and skipping frames too often) while SMPlayer does the job well.

In the future, if and when we upgrade to HD, I will be getting a newer graphics card. The nVidia GeForce 7300 LE looks good. It's low profile (with the appropriate bracket), and has DVI and is not super powerful (though still more than enough capability for playing some games and HD). Apparently it has PureVideo, which means that in WMP and in Linux/VLC I can play HD video on the graphics card. Some users report 50% CPU dropping to 5% as a result of this. We'll see. Currently I'm stuck with Windows XP because of issues with SCART out on Linux. But hopefully I will be able to ditch XP soon, as DVI out shouldn't be too difficult with nVidia cards.

---

### Post by The Funkbomb on 2009-11-06
I rock the E5200.  Hit 3.33ghz by upping the FSB to 266.  No vcore change needed.  Still set at 1.25.  I could probably hit a little higher with no ill effect if I were to bump it up a bit.

---

### Post by lovinglinux on 2009-11-24
Upgraded!!!!!

I've got a Core™ 2 Duo E7500(2.93GHz,3MB) for only U$ 190,00. It was the last one on the shop. 

It is working great!!!! I can watch flash videos now and it only takes 20% of the CPU instead of 100%. Woohooo!!!!!

Thanks everyone for the tips.

:popcorn: \\:D/\\:D/\\:D/

---

