---
title: "Which Thinkpad should I buy? For SCIENCE!"
date: 2014-11-03
forum: The Cafe
---

### Post by Zorgoth on 2014-11-03
So, my laptop broke recently (I still have a desktop, but I certainly don't appreciate sitting in my room all day). My advisor said that the discretionary funds in my research grant could be used on a new one, and said not so spend more than $2,000 including a three year warranty (the funds can also be used for conferences, so cost is still relevant, sadly, but having a budget that is twice what I've ever spent before is pretty amazing).

The only brands I'm allowed to get are Lenovo, Dell, and Apple. I am not impressed with the hardware per unit cost on Apples, and my experience with the build quality of Dells has been terrible. I would be interested in their Precision mobile workstations anyway, except that they take two weeks to ship.

I want to get something reasonably well-built, so I'm thinking Thinkpad. I run Ubuntu LTS and do not use Windows, so Ubuntu support is important, although that hasn't ever been a major issue for me apart from Optimus (why NVIDIA? WHY?).

These are the choices I'm looking at right now:

Lenovo Thinkpad W - better processor, memory and graphics than the T, better everything than the E - $1750 on Lenovo website w/3 year accidental damage protection warranty

- Intel Core i7-4800MQ
- 16GB RAM (four sticks in four memory slots)
- NVIDIA Quadro K1100m w/2GB memory - sadly, this is an Optimus card.
- Has a 16GB mini SSD

Lenovo Thinkpad T - faster processor than E, but no mini SSD - $1500 on website w/same warranty
- Intel Core i7-4700MQ
- 8GB RAM (one SODIMM, two slots)
- Intel HD graphics 4600
- Does not have a 16GB mini SSD

Lenovo Thinkpad E - $1250 on website w/same warranty
- Intel Core i7-4702MQ - a perfectly capable quad core processor
- 8GB RAM in one SODIMM (for $50 less I could get it in two, but this way it would be cheaper to upgrade it in the future if we find that 8GB is not enough)
- Intel HD graphics 4600
- Has a 16GB mini SSD

The other features are not that different between the computers.

Many internet reviews say that the T is a better built machine than lower-end Thinkpads like the E.

Here are my biggest questions:

1. Does anyone have a clear idea what the difference in build quality is likely to be between the W, the T, and the E? I'm hoping to keep this computer for at least three years.

2. Are Quadro cards better supported than standard gaming cards for GPU computing? The only evidence of this that I found is the MATLAB thing saying that Quadro and Tesla cards are good for the parallel computing toolbox.

3. How big of a difference will the 16GB mini SSD make in a) boot time and b) speed of the computer outside of boot time?

4. Any Ubuntu compatibility issues (besides Optimus)?

---

### Post by pqwoerituytrueiwoq on 2014-11-03
quadro is good for certain tasks, on the hardware level is is virtually identical to the gaming series hardware, if you can trick the quadro driver into thinking your GTX card is a quadro card you can run these tasks vastly faster than you could on the normal driver
not sure of the state of the quadro drivers for linux, im sure it is usable by now, but if hte preforamce is worth the money for the hardware i don't have a clue

i would not really bother with a mini ssd, gust replace the HDD or ODD with a 240+GB 2.5" SSD, a 16GB ssd will usually be slow for a ssd, better than a mechanical drive but still, i would need to see the specs on the ssd to tell you about how fast it will be, that 16gb ssd is probably intended for caching the hdd, thought you could use it for a boot drive with linux after changing some bios settings (windwos uses >18gb for a base install compared to under 3 to 8gb for linux, depending on the distro)
a year or 2 ago a cache ssd was not a bad idea when high capacity SSDs were insanely expensive, today a 64gb SSD cost the same as a 16GB ssd a year to two ago did, we now have hybrid HDDd aka SHDD for this target audience

of those 3 CPUs the only one that supports VT-d (basically lets you use virtualbox) is the i7-4800MQ
[http://ark.intel.com/compare/75119,75128,75117](http://ark.intel.com/compare/75119,75128,75117)
edit: they all support VT-x that is probably what VB needs, found out about this type of stuff the hard way, i always check intel CPUs for this now

The i7-4702MQ will give you the best battery life of those 3 being a 37W chip verses a 47W chip

Intel recommends the exact same proce for each of those processors, so the price difference is not in the CPU (at least is should not be)

---

### Post by Zorgoth on 2014-11-03
I don't care too much about battery life, but I do care what happens when my computer is sitting running computations overnight. Is the lower power draw from the i7-4702MQ possibly going to make it higher performance in the long haul (i.e. will the other CPUs get throttled more due to heat)?

The 4800MQ actually costs more than the 4700MQ on the W - I was basing my decision on benchmarks that suggested that 4800MQ was around 10% faster. However I also read two reviews by the same person of two Lenovo Thinkpad Ws, and the one that had the 4800MQ had its speed throttled to a mere 800 MHz under stress (and stress is certainly something that will happen to my CPU), while this did not occur with the 4700MQ.

I was confused about what you said about the SSD (since Lenovo charges $300 for a decent sized one), but after looking up the prices online it makes a lot more sense. My theory was that I would install the OS on the mini SSD, but it looks like if I want an SSD it indeed seems to make more sense to put a full-size one in myself. They're charging over double what the upgrade is worth for the 2.5 inch SSD. Thanks a lot! I do wonder if it might make sense to get a higher capacity M.2 SSD and use it alongside the included HDD? I know that my uncle who does similar work to what I will be doing is majorly into hard drive space.

So this may mean that really I am looking at the W with 4700MQ and no mini SSD for $1570, so I'm paying $70 over the T for a dedicated professional graphics card and double the RAM in double the slots, which seems like a great deal, although the reviews seemed to favor the build quality of the T over the W. The L seems to be made better than the E, so I may replace the lower price point option with that (it has similar specs, but slightly higher cost and apparently longer battery life).

---

### Post by pqwoerituytrueiwoq on 2014-11-03
m.2 is not main stream yet, only common on enthusiast consumer hardware, there is not much competition for that form factor and from what i have seen most m.2 ssds are slower that the 2.5" ones, while the m.2 port can handle double the sata 3 limits, m.2 SSDs can't yet

if you are going to be doing overnight calculations i would suggest using a desktop for that
laptops are for light duty work, desktops are for heavy duty work

all 3 of those cpus support 32gb ram, check if the boards support more than 16
i would expect the boards to max at 8gb per slot
ram cost around $9.37 per gb

---

### Post by /ADM on 2014-11-04
Thinkpad T or E series (NVidia drivers are horrible on Linux) Intel are a much better company to support.  Though have you looked at the X series (I call these the 'real' thinkpads).  The X1-Carbon is a fantastic laptop and my old x200s is still better performing than most laptops on sale today.  Once you buy one, you're pretty much set for a decade (unless you do some gaming).

---

### Post by Zorgoth on 2014-11-04
I was impressed by the X1-Carbon but I don't feel the investment is justified because a) I'm just not that mobile and b) the purpose of the grant is to fund my research for the next two years, so while I'd love to have an ultra-durable machine, any laptop that can be expected to last two-three years is good enough.

I noticed that the Lenovo Thinkpad L's Intel HD 4600 graphics say "with expresscard". What exactly is the purpose of this expesscard slot being associated with the graphics?

---

### Post by mips on 2014-11-04
Better GPU option would be the Intel Iris based GPUs, after that nVidia and finally AMD/ATI.

---

### Post by RichardET on 2014-11-04
I have a W530, 24 GB of memory, 500 GB HD and the 2GB KM1000 Nvidia.  I have had it just shy of two years.  I like it, but I don't suggest it if you want to run any Linux natively on it;  The Nvidia is not setup fr Linux.  I would go with the T series instead, and get a i7 with 16 GB of memory.

---

### Post by Zorgoth on 2014-11-04
I'm leaning towards the L. It's good enough for medium-duty work to run quickly, seems to be well-built with a long battery life, and I can upgrade the hard drive to a decently fast 250gb ssd for $140 on my grant (I have to buy from dell store due to nature of funding) and if I need more than 8G of RAM I can buy it pretty cheaply in the future. However, it has occurred to me that it is also good to have a computer that can have tomorrow instead of two weeks. I can also get a Macbook at education prices and the base model that is probably in stock at the computer store more than meets my requirements and I can have it tomorrow; it's a bit out of budget but I can subsidize since it has some features that are more important for me than my productivity anyway (e.g. weight, iris pro graphics). I am debating the merits and it mostly depends on stuff I don't know like durability and cooling.

---

