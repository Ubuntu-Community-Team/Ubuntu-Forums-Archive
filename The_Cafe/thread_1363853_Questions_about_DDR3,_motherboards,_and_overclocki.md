---
title: "Questions about DDR3, motherboards, and overclocking"
date: 2009-12-25
forum: The Cafe
---

### Post by blueshiftoverwatch on 2009-12-25
I was just checking my [motherboard's website]("http://us.msi.com/index.php?func=proddesc&maincat_no=1&prod_no=1740") and it says "*1600 (OC)*" under what kind of RAM it supports. Later on it says "*Supports four unbuffered DIMM of 1.5 Volt DDR3 800/1066/1333/1600*/1800*/2133* (OC) SDRAM, 16GB Max*".

I bought 4GB (two 2GB sticks) of Kingston HyperX 2000 speed DDR3.

Basically this is the first time I've ever built a computer and this was something I guess I overlooked when selecting all my components.

1600 OC means that it officially supports up to 1600 speed but it can support higher if overclocked, right? At least this is what I'm getting from reading the product page.

So...what does this exactly mean? It doesn't say 2000 under the type of RAM it supports. The closest two are 1800 and 2133. Does this mean that my RAM may be clocked at 2000 but is actually running at 1800? Or is it running at 1600?

Can I overclock my RAM to 2133 speed to take advantage of this? Someone told me that you can't overclock Kingston HyperX RAM. Is doing so dangerous? I'm confused.

---

### Post by sandyd on 2009-12-25
when your overclocking anything, increase by small increments. which means that if you slowly increase it, and it gets to the clock speed w/ no problems, then your good. i learned this when i super overclocked my nvidia card and burnt it out.

oh, and three words i forgot -> liquid cooling system.

---

### Post by Khakilang on 2009-12-25
To me overclock means to push up the processor speed above their recommended speed. But I don't know about the RAM. But becareful when overclocking it will generate heat so extra fan is recommended.

---

### Post by happyhamster on 2009-12-25
> **blueshiftoverwatch said:**
> 1600 OC means that it officially supports up to 1600 speed but it can support higher if overclocked, right? At least this is what I'm getting from reading the product page.
It means that for any higher than 1333 you will have to set things manually.

> 
So...what does this exactly mean? It doesn't say 2000 under the type of RAM it supports. The closest two are 1800 and 2133. Does this mean that my RAM may be clocked at 2000 but is actually running at 1800? Or is it running at 1600?
It's likely running at 1333, at 1.5V and is using some default timings (for example 9-9-9). You'll have to manually select the (overclocked) settings, for example 2000, at 1.65V, 8-8-8 timings. The setttings you can get away with depend on the motherboard and the exact type of RAM you have, I based the above on the datasheet found at:

[http://www.ec.kingston.com/ecom/configurator_new/PartsInfo.asp?root=us&LinkBack=http://www.kingston.com&ktcpartno=KHX2000C8D3T1K2/4GX](http://www.ec.kingston.com/ecom/configurator_new/PartsInfo.asp?root=us&LinkBack=http://www.kingston.com&ktcpartno=KHX2000C8D3T1K2/4GX)

Which may not be the RAM you have.

> 
Can I overclock my RAM to 2133 speed to take advantage of this?
Perhaps, but overclocking above 2000 isn't guaranteed.

> 
Someone told me that you can't overclock Kingston HyperX RAM.
Those sticks are tested by the manufacturer and then sold close to the highest speed it will run at. It's therefore unlikely to find sticks that overclock far beyond their given speed. But sometimes you indeed get lucky :)

> 
 Is doing so dangerous? I'm confused.
Yes. It makes things run hotter (causing stuff to malfunction earlier), and just generally makes your system more unstable. It's possible to do a "safe" overclock of course, by being careful (going step-by-step) and testing a lot (memtest, all kinds of stresstests like mersenne prime, superpi etc).

I never bother to overclock memory: the overall increase in speed you'll see is small, and it's just a pain recovering from a RAM-related crash/lockup (this depends on the BIOS I guess). In other words: I think that overclocking the CPU is a relatively easy and fun process compared to overclocking RAM. 

That's just my opinion though. Good luck.

---

### Post by Skripka on 2009-12-25
> **happyhamster said:**
> 
Yes. It makes things run hotter (causing stuff to malfunction earlier), and just generally makes your system more unstable. It's possible to do a "safe" overclock of course, by being careful (going step-by-step) and testing a lot (memtest, all kinds of stresstests like mersenne prime, superpi etc).

I never bother to overclock memory: the overall increase in speed you'll see is small, and it's just a pain recovering from a RAM-related crash/lockup (this depends on the BIOS I guess). In other words: I think that overclocking the CPU is a relatively easy and fun process compared to overclocking RAM. 

That's just my opinion though. Good luck.

How hard it is to overclock depends greatly on the BIOS, and how much control the CPU grants you.  Fully unlocked Black-Edition AMDs are great because they are cheap, and the only limit on what you can do is the BIOS.

Whether or not overclocking RAM depends greatly on where the bottleneck is.  On my box, it is my RAM and FSB--overclocking those gets me big gains in certain scenarios.  I could push my box more if I went to 2 DIMMs of 2GB each, rather than 4 DIMMs of 1GB each-as AMD CPUs have known problems when using all 4 DIMM slots.

---

### Post by blueshiftoverwatch on 2010-01-14
I just increased my RAM speed from 1333 to 1600 by setting the FSB/DRAM Ratio to the highest it would go without modifying other settings. I have [this fan]("http://www.newegg.com/Product/Product.aspx?Item=N82E16835116021&Tpk=kingston%20fan") above my RAM as well to keep things cooler.

I also increased my Phenom II X4 965 from 3.4GHz to 3.5GHz. I'm afraid to go any higher than that because I don't know anything about the viability of stock coolers and increasing the voltage. I did notice however that when I start up my computer I get error messages about my CPU frequency scaling applets on the Gnome panel not being functional. All 4 of them say 3.5GHz but I can't scale them back anymore, ie switching to OnDemand mode or anything. Not that I would want to anyway. Why is this?

---

### Post by Skripka on 2010-01-14
> **blueshiftoverwatch said:**
> I just increased my RAM speed from 1333 to 1600 by setting the FSB/DRAM Ratio to the highest it would go without modifying other settings. I have [this fan]("http://www.newegg.com/Product/Product.aspx?Item=N82E16835116021&Tpk=kingston%20fan") above my RAM as well to keep things cooler.

I also increased my Phenom II X4 965 from 3.4GHz to 3.5GHz. I'm afraid to go any higher than that because I don't know anything about the viability of stock coolers and increasing the voltage. I did notice however that when I start up my computer I get error messages about my CPU frequency scaling applets on the Gnome panel not being functional. All 4 of them say 3.5GHz but I can't scale them back anymore, ie switching to OnDemand mode or anything. Not that I would want to anyway. Why is this?

Cpufrequtils was not written with overclocking in mind.  All it knows is your default CPU frequency, stepping, and multipler.  If you overclock just using multiplier it should then factor that part of the overclock into account...but cpufrequtils does not worry about FSB speeds, and any overclock done that way will not be seen by it.

I run cpufrequtils, and I dial my machine back to 1.6gHz with ondemand...I know that when needed my machine still goes up to 3.65, from benchmark figures with and without cpufrequtils running.

I OC my machine with a x14.5 multiplier, and the rest done by FSB.  Cpufrequtils tells me my 3.65gHz CPU has a max speed of 2.9gHz, when at full tilt it is actually 3.65

Going 3.5gHz+, I'd strongly advise getting an aftermarket CPU HSF and Arctic Silver--increasing the voltage increases heat.  There are lots of great options on NewEgg, I run a Zalman 9700.

---

