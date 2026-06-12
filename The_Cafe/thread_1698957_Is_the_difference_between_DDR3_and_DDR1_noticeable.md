---
title: "Is the difference between DDR3 and DDR1 noticeable?"
date: 2011-03-03
forum: The Cafe
---

### Post by brawnypandora0 on 2011-03-03
With all other specs being the same (around a 1GHz processor), is there any noticeable difference between 2GB of DDR1 and 2GB of DDR3?

---

### Post by adduds on 2011-03-03
[http://wiki.answers.com/Q/Ddr1_vs_ddr2_vs_ddr3](http://wiki.answers.com/Q/Ddr1_vs_ddr2_vs_ddr3)

[http://ezinearticles.com/?What-is-the-Difference-Between-DDR1-DDR2-and-DDR3?---The-Complete-Idiots-Guide&id=1520597](http://ezinearticles.com/?What-is-the-Difference-Between-DDR1-DDR2-and-DDR3?---The-Complete-Idiots-Guide&id=1520597)

check those two out...

and yes you would notice a large difference it how quickly programs load into ram (memory)  if you have a faster bus ddr3 ie ddr3 running at 2000 mhz

---

### Post by disabledaccount on 2011-03-03
Power consumption difference can be significant, but it depends on module capacity and clocking. Usable bandwidth is higly dependant on architecture and type of application:
- integrated GFX cards are efficiently killing peformance of system memory
- DRAM technology is effective only when using burst (block) transfers, so in many cases difference in speed wont be noticable, but sometimes can be huge. F.e DMA transfers will always be faster, but software can access memory in very random / scattered way, thus without significant performance gain. In fact sometimes newer DDRs can be slower - they have longer timings and needs higher <physical> clocking to read 1byte from random location with acceptable delay.

...edit:
The article linked above is completely mess, as the autor(s) don't understand difference betweent clocking and "clock rating" - thus they say: (f.e.)
> DDR2 memory is the second generation in DDR memory. DDR2 begins with a  speed level of 400MHz as the lowest available while the 400MHz speed is  actually the highest speed for DDR1. Therefore, DDR2 picks up where DDR1  leaves off. It's a bit strange but due to different latencies a 400MHz  DDR1 will outperform a 400MHz DDR2, but the advantage returns to DDR2 as  soon as the speed reaches the next step 532MHz, which DDR1 cannot  reach.
DDR2 have un-proportionally higher timings, so they can outperform DDR400 starting from about ~DDR2-800, but are terribly slow in non-burst operations.

---

### Post by NightwishFan on 2011-03-03
I would say certainly. Doing some experiments I noticed that you can see the hit if the vm is tied up. :)

---

### Post by mips on 2011-03-03
> **brawnypandora0 said:**
> With all other specs being the same (**around a 1GHz processor**), is there any noticeable difference between 2GB of DDR1 and 2GB of DDR3?

NEVER compare processors from different architectures or similar architecture revisions by clock speed. **It means nothing**.

You can have two 1GHz processors from the x86 architecture with one being a bit more modern that will kill the older in performance.  This is even more true between different architectures.

[http://en.wikipedia.org/wiki/Megahertz_myth](http://en.wikipedia.org/wiki/Megahertz_myth)

The fact that you are comparing systems using DDR1 & DDR3 tells me the one system is way older than the other. I can almost guarantee you that the system using newer DDR3 will be MUCH faster than the one using DDR1.

---

### Post by Khakilang on 2011-03-03
I am sure they they vendors had reason to come out with DDR3 and that will be performance.

---

### Post by Paqman on 2011-03-03
> **mips said:**
> 
The fact that you are comparing systems using DDR1 & DDR3 tells me the one system is way older than the other. I can almost guarantee you that the system using newer DDR3 will be MUCH faster than the one using DDR1.

^This.

Most motherboards only support one type of memory, so you're going to be comparing systems from different generations. Apples and oranges, really.

---

### Post by Paqman on 2011-03-03
> **Khakilang said:**
> I am sure they they vendors had reason to come out with DDR3 and that will be performance.

Yes and no. The market's *expectation* of innovation drives demand just as much as actual innovation does. Manufacturers know this, and know they have to at least appear to be constantly making major improvements. Many new technologies in computing aren't really a significant improvement for most users, but to market your products effectively you have to at least be able to claim that they're better than the old stuff.

Just look at IDE vs SATA. On a magnetic hard drive which one you use makes absolutely no difference, but SATA was marketed as "better". It's not until the advent of SSDs that there's actually been a technical reason to use SATA.

The reason they came up with DDR3 was simply to sell motherboards. The fact that's is also slightly faster makes that easier, but they'd still do it even if it wasn't.

---

### Post by mips on 2011-03-03
> **Paqman said:**
> 
Just look at IDE vs SATA. **On a magnetic hard drive which one you use makes absolutely no difference**, but SATA was marketed as "better". It's not until the advent of SSDs that there's actually been a technical reason to use SATA.


:confused:

With the advent of SATA 150, the original spec, there was marginal difference in favour of SATA drive. With each improvement of the SATA standard (SATA 300 etc) the improvements/speeds got MUCH better. And this is all on magnetic media. I also prefer the serial cables, much easier to managed and then there is one way interoperability between SATA & SAS.

---

### Post by disabledaccount on 2011-03-03
> **mips said:**
> :confused:

With the advent of SATA 150, the original spec, there was marginal difference in favour of SATA drive. With each improvement of the SATA standard (SATA 300 etc) the improvements/speeds got MUCH better. And this is all on magnetic media. I also prefer the serial cables, much easier to managed and then there is one way interoperability between SATA & SAS.Drives are faster because of higher data density on the platters, what effects with lower average seek times, seeks number and higer media<->buffer transfers. SATA2 controllers in almost all (if not just all) chipsets are sharing single controller between 2 ports. Furthermore, due to lack of internal dedicated buffers best of them allows to reach max 400-450MB/s for all ports (4-6 in case of Intel ICHx). Besides, todays fas.test HDDs can reach about 140MB/s *peak sequential read* - they can almost fully utilise SATA1, but not SATA2 or 3.

About memory again: <different explanation>
Today's memories have access times about 40-50ns typically. This is *very* long time.
Assuming that Your software wont hit CPU caches and start to read from random locations with bus width 128bits you can reach max 16bytes* (1/50*10^-9) = 16*20000000bytes = ~300MB/s - and this is optimistic, cause we not counting almost continous DMA and IO activity. You can buy DDR6 and it wont help You, unless you optimize the software or find a way to make delays shorter.

:)

---

