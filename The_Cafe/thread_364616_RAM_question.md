---
title: "RAM question"
date: 2007-02-18
forum: The Cafe
---

### Post by maniacmusician on 2007-02-18
When buying RAM, is it better to spread it out over a couple of slots, or is it better to have more memory on one slot? Or does it not make much difference at all?

---

### Post by G Morgan on 2007-02-18
It wouldn't make much difference at all. The chokepoint is the bus itself and the RAM shares that however it is done.

---

### Post by Kindred on 2007-02-18
As far as I understand, It's good to take advantage of dual channel which requires pairs of memory but gives better performance - but can of course mean compromising on the max memory you can actually fit on the board.

---

### Post by spockrock on 2007-02-18
dual channel will give you better performance but of course requires two identical sticks of ram (for the most part) .  You could always just get a large dual channel memory kit. Though.  BTW when running dual channel the bus becomes 128 bits wide where as its just 64bits.

---

### Post by maniacmusician on 2007-02-18
Okay, thanks.

One more question; I'm building a new system. In the past, I've gone with boards that supported DDR2 667. I know I should step it up this time. The system will be a C2D e6600, with at least 2 GBs of RAM. My question is, will I be satisfied with DDR2 800 or should I go for something higher? 

note: keep in mind that the speed of the RAM will also affect which motherboard I buy.

---

### Post by spockrock on 2007-02-18
> **maniacmusician said:**
> Okay, thanks.

One more question; I'm building a new system. In the past, I've gone with boards that supported DDR2 667. I know I should step it up this time. The system will be a C2D e6600, with at least 2 GBs of RAM. My question is, will I be satisfied with DDR2 800 or should I go for something higher? 

note: keep in mind that the speed of the RAM will also affect which motherboard I buy.

uhhh this is where things get tricky, generally as the frequency goes higher the ram is better, but if the latencies are high, then no........if you have high frequency ram with lower latencies then its better to go with the faster ram.   Clock latency just means (simplified) how many clock cycles it takes to do one operation. I am gonna make a really simplified example of this, but an example is say you have two sets of ram one being DDR1 520 with a CL of 3 and DDR2 at 667 with a clock latency of 4.  The DDR1 520 is acctually faster even though the ddr2 module has a higher frequency, but due to the higher latency its not able to do more operations.  I hope that makes sense, so yes and no, if you get DDR667 with low latencies it might be faster then DDR800 with high latencies.  (btw the difference between ddr1, 2 and soon 3 is the voltages they run at more or less and the ability to hit higher frequencies).

Of course the best scenario is high frequency ram with low latencies.

---

### Post by maniacmusician on 2007-02-18
Cool, I understand that.

Now I have to figure out what voltages do and how they figure into the equation.

---

### Post by spockrock on 2007-02-18
> **maniacmusician said:**
> Cool, I understand that.

Now I have to figure out what voltages do and how they figure into the equation.

well lower voltage means less power (generally), also low voltage ram is sometimes preferred by overclockers, because increasing the voltage can mean lowering the timings or running the ram at high speeds.  But if you do not plan on it, then pretty much ignore voltage.

The best way to look at it, is this, how much are you will to spend, and how long you plan on keeping the machine.  How much are you willing to spend, and what do you need, btw good call on 2GB of ram......I really do not suggest going lower then that, especially if you plan on running vista.

---

### Post by maniacmusician on 2007-02-18
I am not getting Vista. lol. I'm fine with just Ubuntu.

I may overclock in the future when I feel more confident about it...so perhaps I should go with lower voltage RAM?

I plan on keeping the machine for a good long while. At least 3 years for a bare minimum. As for how much I'm willing to spend; as much as it takes to get what I need. Of course, I'm tight on cash, so I'll be buying the essentials first and adding parts later. For instance, I'm starting out with 1GB of RAM, and will add more later. I will probably end up going beyond 2. To be on the safe side, I'm making sure my mobo supports at least 8 GB.

For me, the "essentials" so far is coming out to about 500 bucks which is bad news, but I guess I'll have to splurge. 

But on the topic of voltage, from what you've said, it seems that low voltage is the preferred choice. What's considered "low"? 1.8V? 2.0V?

---

### Post by spockrock on 2007-02-18
> **maniacmusician said:**
> I am not getting Vista. lol. I'm fine with just Ubuntu.

I may overclock in the future when I feel more confident about it...so perhaps I should go with lower voltage RAM?

I plan on keeping the machine for a good long while. At least 3 years for a bare minimum. As for how much I'm willing to spend; as much as it takes to get what I need. Of course, I'm tight on cash, so I'll be buying the essentials first and adding parts later. For instance, I'm starting out with 1GB of RAM, and will add more later. I will probably end up going beyond 2. To be on the safe side, I'm making sure my mobo supports at least 8 GB.

For me, the "essentials" so far is coming out to about 500 bucks which is bad news, but I guess I'll have to splurge. 

But on the topic of voltage, from what you've said, it seems that low voltage is the preferred choice. What's considered "low"? 1.8V? 2.0V?

yeah for ddr2 1.8 is the ddr2 operation voltage, (2.5 for ddr1) so I don't expect ram to run at lower voltages by default, but expect to see some of the higher end ram asking for 1.9V or even 2.0V, but they often give better latencies.  The important thing here is latencies and frequencies, some ram chips are great and some medicore.

Also if you plan on overclocking, look at your cpus fsb speed and get faster ram, so if you are getting a e6600 which uses a 266 FSB, so the ram for it would be 533MHz ram, but if you get 667 or 800MHz ram, then you do not have to use a ram divider when going over the spec fsb of the ram.  Out side of athlon64s because of an integrated memory controller its best to run the CPU and RAM at the same FSB.  With 667 ram you can up the FSB to 333 (if the cpu lets you of course) if not you can still run the ram at that speed or what some people try to do is run it at 1:1 and drop the timings on the ram, and that could result in much faster ram.  Also you do not have to oc the ram and leave it at spec speeds and timings, but those are the joys of overclocking, and again oc'ing is of course at your own risk.

---

### Post by FyreBrand on 2007-02-18
> **maniacmusician said:**
> When buying RAM, is it better to spread it out over a couple of slots, or is it better to have more memory on one slot? Or does it not make much difference at all?Another thing to consider is what your motherboard/ram type wants.  Some ram can come in single sticks and others work in pairs better.  It can depend and what your mobo can take and what the ram itself requires.

Read your mobo's tech manual which you should be able to find on their site.  Most have pretty good documentation.  At work we use mostly use Intel with a few VIA.  Both have had pretty good documentation on what works.  Since it's a business environment we doesn't overclock so I don't know anything about that end of it.

---

### Post by maniacmusician on 2007-02-18
So what I'm taking out of all this is that for the purposes of overclocking, the best choice is high frequency, low latency RAM?

I don't know anything about timings yet, though.

I've heard that the record clock for the e6600 was 4.0GHz with good cooling. I probably won't go that high. But I forget what the FSB clock was for that. I may not even overclock at all if I feel like I don't need it..

@FyreBrand: I'm choosing my mobo last, based on other choices like the RAM, video card, etc. So I'll be picking my mobo after picking all these parts.

---

### Post by spockrock on 2007-02-18
> **maniacmusician said:**
> So what I'm taking out of all this is that for the purposes of overclocking, the best choice is high frequency, low latency RAM?

I don't know anything about timings yet, though.

I've heard that the record clock for the e6600 was 4.0GHz with good cooling. I probably won't go that high. But I forget what the FSB clock was for that. I may not even overclock at all if I feel like I don't need it..

@FyreBrand: I'm choosing my mobo last, based on other choices like the RAM, video card, etc. So I'll be picking my mobo after picking all these parts.

on air, I have seen most people hit 3.0GHz, the higher clocks are done with water and phase change cooling.  Umm...I doubt you will notice it besides playing games and of course everyones favourite game [sarcasm]bench marks[/sarcasm] :p, I do it cause its just a fun thing for me to do.....but yeah its not really necessary.

---

