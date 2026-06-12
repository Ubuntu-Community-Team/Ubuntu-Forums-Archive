---
title: "What's the point of intel atom?"
date: 2009-08-22
forum: The Cafe
---

### Post by praveesh on 2009-08-22
The intel atom is getting more popularity in the netbooks. But I wonder what it's advantage over the older processors like pentium 4 which are cheap as well as of more powerful than the atom. What you all think?

---

### Post by xuCGC002 on 2009-08-22
The Atom uses very little power, making it ideal for computers such as netbooks or mini-ITX. Pentium 4 (is pretty much retired, BTW) is more oriented for desktops and much larger laptops, using an average amount of power. I'm pretty sure it would drain a small netbook battery in minutes.

---

### Post by Chronon on 2009-08-22
Lower power consumption is the main reason, I think.  (Also smaller size)

---

### Post by nomnomnom on 2009-08-22
I actually want to get an Atom Dualcore mini DTX board.....

---

### Post by cascade9 on 2009-08-22
You really dont NEED as much power as even a p4. Sure, powers nice, but anything over about 1.5Ghz is power enough for most everything.

Low power is the whole point of the atom, and it does that pretty well. Its not just battery life, etc, its also heatsink size and weight, etc. Most of the atoms have TDP (Thermal design power) of 2.5watts, they barely need heatsinks.

---

### Post by cariboo on 2009-08-22
I have an atom powered media center pc, there is no heatsink or fan on the cpu, but the gpu does have a good sized heatsink and fan. My system has a 60 watt power supply, which may be to much. The only complaint I have is that the case fan is to noisy, once the weather gets back to normal, I'm going to disconnect it to see what difference it makes.

---

### Post by praveesh on 2009-08-22
So , what are the advantages of an arm processor. Isn't it also getting some attention?

---

### Post by Chronon on 2009-08-22
cascade9: Watts == power

;)

You mentioned clock speed in your first sentence, so I wanted to clear that up.  Power does not refer to any specific number of computations per second.  It refers to how much energy it dissipates (in the form of heat) per unit time.

A big issue is that old architectures didn't really focus very much on the interconnect geometry or layout.  As feature size gets smaller, you end up with a situation where most of the power dissipation comes in the metallic interconnects between transistors and other elements in the chip.  Making a wire thinner will cost you more power because the resistance increases, for instance.  By designing circuits so that the interconnects can remain as short and fat as possible, you can optimize the power consumption by a given number of circuit elements.  I believe this is one of the differences that leads the Atom to have lower power consumption than the P4.

---

### Post by Chronon on 2009-08-22
> **praveesh said:**
> So , what are the advantages of an arm processor. Isn't it also getting some attention?

ARM is a totally different architecture (not x86 compatible).  ARM processors tend to have low power requirements and are currently the most popular architecture for portable media players.

---

### Post by Warpnow on 2009-08-22
If you put a P4 in a netbook it would get 30 minutes of battery life and catch on fire.

---

### Post by Glenn Jones on 2009-08-22
ARM processors tend to be in imbeded systems eg. microwaves, toasters, mobile phones etc. 

Also don't ARM sell more processors than anyone else in the world?

---

### Post by Chronon on 2009-08-22
[QUOTE=Wikipedia]As of 2009, ARM processors account for approximately 90% of all embedded 32-bit RISC processors. ARM processors are used extensively in consumer electronics, including PDAs, mobile phones, iPods and other digital media and music players, hand-held game consoles, calculators and computer peripherals such as hard drives and routers.[/QUOTE]

Some more info on prevalence of ARM. . .

---

### Post by Lux Perpetua on 2009-08-22
> **xuCGC002 said:**
> The Atom uses very little power, making it ideal for computers such as netbooks or mini-ITX.Also, low power consumption is the key to scalability (think parallel computation). There's a lot of active research these days centered around that idea.

---

### Post by praveesh on 2009-08-23
I haven't thought the low power consumption is this much important. Now Iam eager to know the time upto which the battery of an atom powered netbook would last , if used continuously.

---

### Post by Skripka on 2009-08-23
> **praveesh said:**
> I haven't thought the low power consumption is this much important. Now Iam eager to know the time upto which the battery of an atom powered netbook would last , if used continuously.

Well an Atom N280 netbook, such as the MSi Wind U123 (paired with a 9 cell Li-ion battery) that I have on order from Chez NewEgg, can get 9 hours or so on a charge.

---

### Post by inobe on 2009-08-23
not just long battery life' going "green' a lot to do with it, if anyone noticed it can be utilized with desktops as well.


the atom kinda beats a p4 in the dirt for desktops

---

### Post by moster on 2009-08-23
> **inobe said:**
> not just long battery life' going "green' a lot to do with it, if anyone noticed it can be utilized with desktops as well.


the atom kinda beats a p4 in the dirt for desktops

Atom is power efficient but it is also slow as snail.

Super Pi 1MB
Atom 270 1.6Ghz =  80 sec
E7300 = 15 sec
E5200 = 20 sec

So, you can see, differences are drastic. And I compare it to low-middle end desktop CPUs.

---

### Post by inobe on 2009-08-23
lets compare wattage to performance, lower the wattage on the p4 :)

---

### Post by praveesh on 2009-08-23
> **Skripka said:**
> Well an Atom N280 netbook, such as the MSi Wind U123 (paired with a 9 cell Li-ion battery) that I have on order from Chez NewEgg, can get 9 hours or so on a charge.

OK . But what about the battery life of a laptop powered with a core2duo.

---

### Post by mcduck on 2009-08-23
Intel Mobile Atom N270, 1,6GHz: **2,5W**
(0,75V-1,1V, 3A max)

Mobile Core 2 Duo P8400, 2x2,26GHz: **25W**
(0,85V-1.25V, 38A max)

Mobile Pentium 4 518, 1,8GHz: **88W**  
(1,25V-1,4V, 80A max)

...it's pretty easy to see why the Atom is the way to go for netbooks. Considering that nobody will be able to to any too heavy work on such a small screen anyway..

---

### Post by cascade9 on 2009-08-23
> **Chronon said:**
> cascade9: Watts == power

;)

You mentioned clock speed in your first sentence, so I wanted to clear that up.  Power does not refer to any specific number of computations per second.  It refers to how much energy it dissipates (in the form of heat) per unit time.

A big issue is that old architectures didn't really focus very much on the interconnect geometry or layout.  As feature size gets smaller, you end up with a situation where most of the power dissipation comes in the metallic interconnects between transistors and other elements in the chip.  Making a wire thinner will cost you more power because the resistance increases, for instance.  By designing circuits so that the interconnects can remain as short and fat as possible, you can optimize the power consumption by a given number of circuit elements.  I believe this is one of the differences that leads the Atom to have lower power consumption than the P4.

Its not just the internal connectors, etc, that determine how much TDP you will have..or even how much 'power' (CPU power that is). It does play a role, yes, but Atoms run very low voltage as well as quite low clockspeeds. 

I really shouldnt have said clockspeed, theres more factors than that..cache in particular. Thats why my Athlon +2200 (1795mhz, 256K, 1.65volt) was slower than my Athlon +2500 (1826mhz, 512K, 1.65volt) even though the TDP is almost exactly the same. (62watt vs 62.3watt). Funny enough, my current +4800 (2500mhz, 1MB, 1.325volt) is pretty much the same TDP. 

Interesting how different some benchmarks can be-

1M SuperPi

2.4Ghz Core2Quad- 0.22
2.13Ghz Core2CDuo- 0.24
3.0Ghz Athlon 64 x2- 0.29
1.8Ghz Core2Duo- 0.38
1.8Ghz Phenom x4- 0.42
1.73Ghz PM- 0.46
2.4Ghz P4- 1.08
900mhz Celeron M- 1.28
1.6Ghz Atom- 1.48
1.13Ghz Tualatin- 1.55 

[http://www.mydigitallife.info/2008/03/08/intel-atom-initial-benchmarking-data-vs-pentium-and-celeron-m-processors-before-official-release/](http://www.mydigitallife.info/2008/03/08/intel-atom-initial-benchmarking-data-vs-pentium-and-celeron-m-processors-before-official-release/)

mcduck- I have seen 22'' screens hooked up to netbooks, with a user pounding away at some nasty software and complaining about how slow it is (I nearly fell over when I saw someone running iTunes, DVD shrink + AutoGK on some poor asus eeepc)

---

### Post by hessiess on 2009-08-23
> **praveesh said:**
> So , what are the advantages of an arm processor. Isn't it also getting some attention?

ARM is a much simpler architecture(RISC, fewer instructions) and is still far more power effechent than any x86 chip. and as a bonus it wont run outdated junky OS's like XP.

---

### Post by cascade9 on 2009-08-23
> **hessiess said:**
> ARM is a much simpler architecture(RISC, fewer instructions) and is still far more power effechent than any x86 chip. and as a bonus it wont run outdated junky OS's like XP.

I realy hope that was humour, as theres a boatload of netbooks with atoms + XP

---

### Post by moster on 2009-08-23
> **cascade9 said:**
> I realy hope that was humour, as theres a boatload of netbooks with atoms + XP

hm, what is wrong with his statement? ARM cpus are using less then 1W and XP is dead. Those kicking from XP you see is because nerves are still active :D

---

### Post by cascade9 on 2009-08-23
Whats wrong? "and as a bonus it wont run outdated junky OS's like XP." You may or may not like XP, but to say it wont run on Atom is totally factually wrong. 

Netbooks in general are part of the reason why microsoft extened XP- too keep people from moving to linux (and gain another foothold for linux, as a lack of previous use is one of the factors holding linux back).

---

### Post by Sporkman on 2009-08-23
> **cascade9 said:**
> Whats wrong? "and as a bonus it wont run outdated junky OS's like XP." You may or may not like XP, but to say it wont run on Atom is totally factually wrong. 

Netbooks in general are part of the reason why microsoft extened XP- too keep people from moving to linux (and gain another foothold for linux, as a lack of previous use is one of the factors holding linux back).

Reading comprehension - look into it. ;)

(He said ARM, not Atom.)

---

### Post by hessiess on 2009-08-23
> **cascade9 said:**
> I realy hope that was humour, as theres a boatload of netbooks with atoms + XP

That was not intended as humour, and in computing terms XP is an antique, its 8~ years old! ARM is a much better architecture than X86, however it wont gain any major market share in the desktop market until windows ether supports architectures besides the bloated and out of date x86 platform, or goes away.

And yes, x86 is bloated and dated, it has support right back to the 16 bit days, which is totally uneoserry.

---

### Post by sandyd on 2009-08-23
> **cascade9 said:**
> Its not just the internal connectors, etc, that determine how much TDP you will have..or even how much 'power' (CPU power that is). It does play a role, yes, but Atoms run very low voltage as well as quite low clockspeeds. 

I really shouldnt have said clockspeed, theres more factors than that..cache in particular. Thats why my Athlon +2200 (1795mhz, 256K, 1.65volt) was slower than my Athlon +2500 (1826mhz, 512K, 1.65volt) even though the TDP is almost exactly the same. (62watt vs 62.3watt). Funny enough, my current +4800 (2500mhz, 1MB, 1.325volt) is pretty much the same TDP. 

Interesting how different some benchmarks can be-

1M SuperPi

2.4Ghz Core2Quad- 0.22
2.13Ghz Core2CDuo- 0.24
3.0Ghz Athlon 64 x2- 0.29
1.8Ghz Core2Duo- 0.38
1.8Ghz Phenom x4- 0.42
1.73Ghz PM- 0.46
2.4Ghz P4- 1.08
900mhz Celeron M- 1.28
1.6Ghz Atom- 1.48
1.13Ghz Tualatin- 1.55 

[http://www.mydigitallife.info/2008/03/08/intel-atom-initial-benchmarking-data-vs-pentium-and-celeron-m-processors-before-official-release/](http://www.mydigitallife.info/2008/03/08/intel-atom-initial-benchmarking-data-vs-pentium-and-celeron-m-processors-before-official-release/)

mcduck- I have seen 22'' screens hooked up to netbooks, with a user pounding away at some nasty software and complaining about how slow it is (I nearly fell over when I saw someone running iTunes, DVD shrink + AutoGK on some poor asus eeepc)
hmm... never saw that before

core2duo can beat AMD X4 
hahahaha

---

### Post by cascade9 on 2009-08-23
> **Sporkman said:**
> Reading comprehension - look into it. ;)

(He said ARM, not Atom.)

Oh yeah, it was ARM, not atom. I fail at reading (though strangely, this was a thread abut the Atoms so I guess I just saw the cpital 'A' and ran from there. Damned dyslexia) That changes everything, your looking at windows CE-based windows mobile.

---

### Post by snowpine on 2009-08-23
> **cascade9 said:**
> Oh yeah, it was ARM, not atom. I fail at reading (though strangely, this was a thread abut the Atoms so I guess I just saw the cpital 'A' and ran from there. Damned dyslexia) That changes everything, your looking at windows CE-based windows mobile.

Windows has a Christian Edition? ;)

---

### Post by RabbitWho on 2009-08-23
When I bought my computer I thought core duo and dual core were the same thing. Damnit. It's an easy mistake to make! It's practically the same name!

---

### Post by Skripka on 2009-08-23
> **RabbitWho said:**
> When I bought my computer I thought core duo and dual core were the same thing. Damnit. It's an easy mistake to make! It's practically the same name!

You gotta love branding.  I always liked the 80X86 nomenclature myself.

---

### Post by mcduck on 2009-08-23
> **carlee said:**
> hmm... never saw that before

core2duo can beat AMD X4 
hahahaha

sure, unless you try running 4 instances of SuperPi at the same time.. ;)

(SuperPi runs on a single thread, so it only uses one core on multicore processors)

---

