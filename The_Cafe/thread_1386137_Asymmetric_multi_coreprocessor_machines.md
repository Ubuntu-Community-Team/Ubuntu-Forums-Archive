---
title: "Asymmetric multi core/processor machines"
date: 2010-01-20
forum: The Cafe
---

### Post by hwttdz on 2010-01-20
Why is there not a move towards asymmetric multi core/processor machines?  let me explain what I mean.  I have a machine that has a huge processor, which is sometimes terribly underutilized, and though the new intel chips can clock down cores and save power that way nothing compares to turning the cores off.  So I'm wondering why there's no intel atom/intel core i7 board where the atom chip is powered up all the time, and the i7 chip is powered up as needed.  I'm imagining that this would save on the order of 40-50 watts, which for a 24-7 machine could mean some pretty serious power savings and cost savings given that the secondary chip is super cheap to start with.  One could also imagine this all happening on one chip where one core is anemic relative the others.

---

### Post by MaxIBoy on 2010-01-20
Everyone has an asymmetric multiprocessing machine. In higher-end gaming rigs, the power is grossly biased toward the graphics hardware (with an opposite bias on low-end hardware,) but both the GPU and CPU are capable of general-purpose computation.

Or, you can look no further than your iPhone/iPod touch (if you own one.) Unless I'm wrong, there is an ARM11 main CPU which does most of the work, and an auxiliary ARM7 CPU with a lower clock (lower power usage) that gets used for audio decoding and the like. If all you are doing is listening to music, than the main CPU can idle and save power.

If I recall correctly, there was also talk of introducing hybrid x86/ARM motherboards for Windows/Linux dualbooting netbooks. It would be pretty cool to use a superior ARM core most of the time, but also have an x86 chip for running Windows programs in WINE.

However, shifting everything from CPU to CPU would result in at least a quarter-second (and probably more of a half-second) pause. For me at least, this would be a total showstopper.

---

### Post by Skripka on 2010-01-20
> **hwttdz said:**
> Why is there not a move towards asymmetric multi core/processor machines?  let me explain what I mean.  I have a machine that has a huge processor, which is sometimes terribly underutilized, and though the new intel chips can clock down cores and save power that way nothing compares to turning the cores off.  So I'm wondering why there's no intel atom/intel core i7 board where the atom chip is powered up all the time, and the i7 chip is powered up as needed.  I'm imagining that this would save on the order of 40-50 watts, which for a 24-7 machine could mean some pretty serious power savings and cost savings given that the secondary chip is super cheap to start with.  One could also imagine this all happening on one chip where one core is anemic relative the others.

Why? Because in this case i7 and Atom are two COMPLETELY different CPU architectures that are COMPLETELY incompatabile...and require two COMPLETELY different motherboards and DDR memory types.


CPU throttling does the same job and is cheaper...and is physically possible.  Just because I have a 3.65 gHz quad-core doesn't mean that it is always operating at full tilt wasting juice.  Most of the time it is idle at 800mHz.

---

### Post by Xbehave on 2010-01-20
Im not sure turning cores off on a single chip is worth it and multichip boards have gone out of fashion since multicore chips came in. The targets markets of i7 (high end gaming rigs/heavily used servers/etc) and atom (netbooks) are quite different so the cross over is minimal.

---

### Post by MaxIBoy on 2010-01-20
Actually, atom and i7 are both i786, with about the same instruction set. But it would be so difficult to pull off, that I doubt it's really such a hot idea. Why not buy a comparatively weak CPU and then use OpenCL acceleration on your graphics card? Both nVidia and ATI drivers support this on Linux now. We just need Gallium3D to get more mature, and we will have *open-source* OpenCL acceleration on Intel, nVidia, and ATI graphics hardware, as well as a software implementation if we really need it.

---

### Post by hwttdz on 2010-01-20
> **Skripka said:**
> Why? Because in this case i7 and Atom are two COMPLETELY different CPU architectures that are COMPLETELY incompatabile...and require two COMPLETELY different motherboards and DDR memory types.


CPU throttling does the same job and is cheaper...and is physically possible.  Just because I have a 3.65 gHz quad-core doesn't mean that it is always operating at full tilt wasting juice.  Most of the time it is idle at 800mHz.

Ok, I appreciate the differences in architecture between atom and i7, but it should be possible between say atom and c2q.  Or perhaps in some new generation of chips.  

I'm not terribly impressed with the throttling on my machine, 1.6 to 2.5 Ghz, what I propose is turning cores off entirely, while a 40% savings is nice, it doesn't compare to 75% (3/4 cores off)+ 0.4*25 (final core downclocked) = 85% or the even better number that could be achieved with asymmetric processors/cores.

I'm not saying this is possible today, I'm saying I think it seems an attractive idea.

---

### Post by hwttdz on 2010-01-20
> **Xbehave said:**
> Im not sure turning cores off on a single chip is worth it and multichip boards have gone out of fashion since multicore chips came in. The targets markets of i7 (high end gaming rigs/heavily used servers/etc) and atom (netbooks) are quite different so the cross over is minimal.

I just think mr high end gamer might not mind having to fork up an extra $40 or so for a super weak but super power efficient cpu in order to save maybe double that a year on electricity.

---

### Post by Skripka on 2010-01-20
> **hwttdz said:**
> Ok, I appreciate the differences in architecture between atom and i7, but it should be possible between say atom and c2q.  Or perhaps in some new generation of chips.  

I'm not terribly impressed with the throttling on my machine, 1.6 to 2.5 Ghz, what I propose is turning cores off entirely, while a 40% savings is nice, it doesn't compare to 75% (3/4 cores off)+ 0.4*25 (final core downclocked) = 85% or the even better number that could be achieved with asymmetric processors/cores.

I'm not saying this is possible today, I'm saying I think it seems an attractive idea.

In theory it would be possible.  Dual LGA775 and LGA1366 server boards are available....but you'd need a full-size tower, and extendedATX board to fit it....and most people don't like having computers that don't fit under or on their desk.

It also add immensely to complexity of code and management of hardware....for not that much gain.
D

---

### Post by MaxIBoy on 2010-01-20
> **hwttdz said:**
> I just think mr high end gamer might not mind having to fork up an extra $40 or so for a super weak but super power efficient cpu in order to save maybe double that a year on electricity.
Speaking as a high-end gamer, I would be more interested in the reduction of excess heat production.

---

### Post by hwttdz on 2010-01-20
> **MaxIBoy said:**
> Actually, atom and i7 are both i786, with about the same instruction set. But it would be so difficult to pull off, that I doubt it's really such a hot idea. Why not buy a comparatively weak CPU and then use OpenCL acceleration on your graphics card? Both nVidia and ATI drivers support this on Linux now.

But then you get into the question of what can the video card do to save power?  I'm familiar with some laptops which have both integrated and dedicated graphics solutions and can switch on the fly.  That would be pretty much ideal, it would be using the graphics card as the high power processor (both in performance and electricity terms), and the cpu as the low power processor.  Of course I'm not familiar with this openCL...

---

### Post by Skripka on 2010-01-20
> **hwttdz said:**
> I just think mr high end gamer might not mind having to fork up an extra $40 or so for a super weak but super power efficient cpu in order to save maybe double that a year on electricity.

Electricty ain't that expensive.  Having a 1000W gaming rig going full tilt for an hour in the US costs about $0.10  It adds up but few people have their nuclear-reactor powered 2kW computer going full tilt 24/7/365.

---

### Post by hwttdz on 2010-01-20
> **MaxIBoy said:**
> Speaking as a high-end gamer, I would be more interested in the reduction of excess heat production.

Well this would have no effect on heat while gaming/under load, and might in fact make things worse (though adding less than 10 W is likely a drop in the proverbial bucket). But otherwise it would reduce heat as well.  Out of curiosity do you know the power consumption numbers of your machine, mine is at 115 watts or so (which seems unnecessarily high to me, i7, gt240).

---

### Post by MaxIBoy on 2010-01-20
You're not familiar with openCL? You should really be reading Phoronix more. ;) Here's a list of every article they have on the topic:
[http://www.phoronix.com/scan.php?page=search&q=OpenCL](http://www.phoronix.com/scan.php?page=search&q=OpenCL)

I don't fully understand how these GPUs work under the hood but I do know that my 4850 idles at 45°C while reaching up to 110°C under extreme load (about 90°C with normal gaming.) This is indicates that *some* kind power-saving techniques are being used.

I haven't measured power usage on it. Specs are Phenom x4 9550 (overclocked slightly,) MSI R4850 (essentially a 4850 with aftermarket fan out of the box,) and the power supply is 500 watts with a 12cm exhaust fan. Everything goes in an Xclio Windtunnel case with dual 25cm intake side fans and a 9cm rear panel exhaust fan, plus I plan on adding a 10cm front intake fan. I also use dual monitors (one CRT @ 75 watts, one LCD @ 25 watts if I recall correctly,) and that should not be ignored either. This whole assembly uses enough that if you put it on the same power circuit as a 800 watt laser printer and run the computer under load, it halts when you try to print something (despite the UPS!) I imagine that under full load, the computer without the monitors is probably using something like 350-400 watts, and idling at maybe 150 watts. I don't know for sure. Anyway, that thing is LOUD, so there's no way I'm leaving it on 24/7 (otherwise I couldn't sleep.) These days it's packed away under my desk, because it uses up so much room and I don't have time for gaming anyway.

---

### Post by Xbehave on 2010-01-20
> **Skripka said:**
> Why? Because in this case i7 and Atom are two COMPLETELY different CPU architectures that are COMPLETELY incompatabile...and require two COMPLETELY different motherboards and DDR memory types.
While they use different microarchitectures and different sockets, they use the same arch x86_64 (some atoms are x86 but that's hardly "COMPLETELY COMPLETELY incompatibility"[sic]) and neither processor cares what memory you use.

> CPU throttling does the same job and is cheaper...and is physically possible.  Just because I have a 3.65 gHz quad-core doesn't mean that it is always operating at full tilt wasting juice.  Most of the time it is idle at 800mHz.
Turning off individual Cores can be made possible and even at low clock rates an 800mHz i7 will draw more watts than the 3/4 an atom draws, so while it's not needed OPs idea is valid.

---

### Post by hwttdz on 2010-01-20
> **Skripka said:**
> Electricty ain't that expensive.  Having a 1000W gaming rig going full tilt for an hour in the US costs about $0.10  It adds up but few people have their nuclear-reactor powered 2kW computer going full tilt 24/7/365.

Well we'll call it 0.117 nationwide, but if you're lucky enough to live in New York, you're looking at 0.2.  ([http://www.eia.doe.gov/cneaf/electricity/epm/table5_6_a.html](http://www.eia.doe.gov/cneaf/electricity/epm/table5_6_a.html)), say my machine is on 24/7 that's 8760 hours * (proposed 50 watt savings, diff between idling i7 and idling atom) * 0.2/kwh * 1 kw/1000w = 8760 * 50 * 0.2 * 1/1000 = $87/yr, so surely I do exaggerate.  But still 6 months to pay itself off, and more people than you might imagine leave a cpu on year round.  Call it 8 hours a day even and it takes you what 17 months to break even (and be friendlier to the environment doing it).  

<jest>And finally it's not the nuclear powered machines that I'm talking about they already have such clean power it's a non issue</jest>.

---

### Post by hwttdz on 2010-01-20
> **Xbehave said:**
> ... so while it's not needed OPs idea is valid.

There are lots of things that are not and will never be needed needed, like any more memory than 640k (see Bill Gates).

---

### Post by MaxIBoy on 2010-01-20
> **hwttdz said:**
> Well we'll call it 0.117 nationwide, but if you're lucky enough to live in New York, you're looking at 0.2.  ([http://www.eia.doe.gov/cneaf/electricity/epm/table5_6_a.html](http://www.eia.doe.gov/cneaf/electricity/epm/table5_6_a.html)), say my machine is on 24/7 that's 8760 hours * (proposed 50 watt savings, diff between idling i7 and idling atom) * 0.2/kwh * 1 kw/1000w = 8760 * 50 * 0.2 * 1/1000 = $87/yr, so surely I do exaggerate.  But still 6 months to pay itself off, and more people than you might imagine leave a cpu on year round.  Call it 8 hours a day even and it takes you what 17 months to break even (and be friendlier to the environment doing it).  

<jest>And finally it's not the nuclear powered machines that I'm talking about they already have such clean power it's a non issue</jest>.A gaming rig, the only kind of machine where power is a concern, is going to be way past obsolete in 17 months anyway. (Yes, I know, I'm a hypocrite given my machine's specs-- I'm going to be upgrading it when I get some money. )

---

### Post by hwttdz on 2010-01-20
> **MaxIBoy said:**
> A gaming rig, the only kind of machine where power is a concern, is going to be way past obsolete in 17 months anyway. (Yes, I know, I'm a hypocrite given my machine's specs-- I'm going to be upgrading it when I get some money. )

Well I use my machine as a server (ssh and web) and I'd sure appreciate saving on the order of $90 a year, and I'd be more than happy to fork up the $50 for the atom cpu to have the savings accrue.  But then again I'm the sort of person who gets excited about the 92% efficient power supply and writes scripts to auto-hibernate machines.

---

### Post by Xbehave on 2010-01-20
> **hwttdz said:**
> There are lots of things that are not and will never be needed needed, like any more memory than 640k (see Bill Gates).
But the benefits of your proposal don't justify the increased cost of having two cores, new desktop processors (since p4s anyway) tend to scale down when not in use so they don't draw that much power (and while in use your not going to save power anyway). Basically while it's a cool idea there is no market for such a combo.

---

### Post by Skripka on 2010-01-20
I was curious this time ;)

> **Xbehave said:**
> While they use different microarchitectures and different sockets, they use the same arch x86_64 (some atoms are x86 but that's hardly "COMPLETELY COMPLETELY incompatibility"[sic]) and neither processor cares what memory you use.


i7 uses DDR3 and triple channel memory.  Atom is only for mid frequency DDR2 (My Atom N270 MSi Wind uses 500-600mHz DDR2 IIRC) in double channel memory.  I'd call that complete incompatibility.  We aren't even speaking about FSB architecture and memory controllers.

You'd have better luck with getting C2Quads and Atoms to play nice...but then you'd have another set of headaches...in addition that you'd be stuck using already obsolete CPUs and memory.

We also aren't speaking about the coming move of the GPU onto the CPU die that Intel is currently cooking up-which throws another wrench into all this.  I'm willing to bet ideas like this have been tossed around at AMD and Intel, and killed due to great complexity added and little gain in the long run.

---

### Post by MaxIBoy on 2010-01-20
> **hwttdz said:**
> Well I use my machine as a server (ssh and web) and I'd sure appreciate saving on the order of $90 a year, and I'd be more than happy to fork up the $50 for the atom cpu to have the savings accrue.  But then again I'm the sort of person who gets excited about the 92% efficient power supply and writes scripts to auto-hibernate machines.I run my PII webserver off an 80-watt PSU. Works perfectly fine.

---

### Post by Frak on 2010-01-20
> **MaxIBoy said:**
> Actually, atom and i7 are both i786, with about the same instruction set.

Just little nitpick here, they're both i986 processors. i786 was Netburst, i886 was Core, and i986 is the Nehalem.

As for the OP, changing jobs to and from the processors would not only slow down operations, it would require the host OS to support hotpluggable processors, as the OS would need to unload before one processor was unplugged and another was activated.

---

### Post by MaxIBoy on 2010-01-20
Really? Then why not call it the "core i9?" That would make more sense.

---

### Post by Frak on 2010-01-20
> **MaxIBoy said:**
> Really? Then why not call it the "core i9?" That would make more sense.
Intel is a Silly Goose? I guess because they expose their processor as an i786 to the host. Underneath, they are a lot more efficient.

---

### Post by hwttdz on 2010-01-20
> **MaxIBoy said:**
> I run my PII webserver off an 80-watt PSU. Works perfectly fine.

And you don't view that as 75 watts that you might be saving?

> **Xbehave said:**
> But the benefits of your proposal don't justify the increased cost of having two cores

You mean you disagree with my math? (which is quite likely in err), but you might as well share where I seem to be going wrong, because for me personally it looks like the break even point would be somewhere around 12 months. 

Or that it doesn't make sense for intel or amd to develop such a thing?

> **Frak said:**
> As for the OP, changing jobs to and from the processors would not only slow down operations, it would require the host OS to support hotpluggable processors, as the OS would need to unload before one processor was unplugged and another was activated.

I was imagining something where different processes ran on different cpu's, as the processes already seem to be able to swap from one core to another.  When all the processes "fit" on the small processor the large one is powered off, when you run out of space you power up the large one and start moving threads onto it.  So the small processor is always on.

---

### Post by Frak on 2010-01-20
> **hwttdz said:**
> I was imagining something where different processes ran on different cpu's, as the processes already seem to be able to swap from one core to another.  When all the processes "fit" on the small processor the large one is powered off, when you run out of space you power up the large one and start moving threads onto it.  So the small processor is always on.

You can't just "turn off" CPUs without the host being notified and preparing for the removal. Especially when you are working with two different processors, it just makes the whole scene a mess, and does more harm than good. Sure it could save power, but at the cost of extremely higher latency.

---

### Post by MaxIBoy on 2010-01-20
> **hwttdz said:**
> And you don't view that as 75 watts that you might be saving?No not really. 80 watts is spectacularly efficient in my opinion, and the server probably idles at closer to 40 or 50.

In fact, the reason why my $700 laptop sucks so badly is because of the obsession with power consumption on the part of the designers. The price turned out to be pretty far out of scale with the true performance of the machine (heck, that gaming rig only has about $800 worth of parts in it, less given the passage of time, but it outperforms the laptop about 10 times over.) And they somehow got the battery life down to an hour and 15 minutes anyway. Now that's talent!

> I was imagining something where different processes ran on different cpu's, as the processes already seem to be able to swap from one core to another.  When all the processes "fit" on the small processor the large one is powered off, when you run out of space you power up the large one and start moving threads onto it.  So the small processor is always on.This only works for huge clusters, where each "thread" is enough to bring an entire CPU to its knees. Anything less than that, and the overhead of moving things around is too much. You are talking about at least 40 milliseconds to switch a process between CPUs, which is a vast amount of time during which the process is idle. Even switching a process between multiple cores of the same CPU can be a [huge performance problem]("http://www.linuxjournal.com/article/6799"). Process affinity was introduced into the Linux 2.6 kernel specifically to prevent processes being shuffled around too much, which caused major slowdowns on multicore and multi-CPU systems. Add to that the complexity of slightly different CPUs and translating between them, and you've just turned a modern machine into a Pentium Pro performance-wise. If you batch all the process up and switch them all at once, you will get frequent periods of at least a half-second where the screen locks up and you can't do anything. Are you willing to put up with this happening two or three times an hour? I wouldn't be.

---

### Post by ssam on 2010-01-20
some systems already do this, GPUs, AmigaOne X1000 coprocessor, FPGA coprocessor boards.

> **MaxIBoy said:**
> I run my PII webserver off an 80-watt PSU. Works perfectly fine.

My beagle board runs off the power from a USB hub, and only draws about 1 watt. though you will need a few more watts for a usb hard disk (if it runs from a single usb port it must be under 2.5 W).

---

### Post by markp1989 on 2010-01-20
> **Skripka said:**
> Why? Because in this case i7 and Atom are two COMPLETELY different CPU architectures that are COMPLETELY incompatabile...and require two COMPLETELY different motherboards and DDR memory types.


CPU throttling does the same job and is cheaper...and is physically possible.  Just because I have a 3.65 gHz quad-core doesn't mean that it is always operating at full tilt wasting juice.  Most of the time it is idle at 800mHz.


im sure the op is aware that atom and i7 are way differnt, was just using them as an example . but i do like his idea.

having a low powered cpu for when the system is idle, and a heavy cpu that can spend most of its time idle,  that way you get the best of both worlds, high power when its needed, and low power usage when it isnt. it seems very logical, ofcourse the motherboard would have to support all this stuff, would be good for streaming servers, that need to re encode on the fly.

---

### Post by Frak on 2010-01-20
> **markp1989 said:**
> im sure the op is aware that atom and i7 are way differnt, was just using them as an example . but i do like his idea.

having a low powered cpu for when the system is idle, and a heavy cpu that can spend most of its time idle,  that way you get the best of both worlds, high power when its needed, and low power usage when it isnt. it seems very logical, ofcourse the motherboard would have to support all this stuff, would be good for streaming servers, that need to re encode on the fly.
I see absolutely no reason to use a low powered CPU alternative when all that is needed is to heavily underclock the current CPU when it's not in use.

---

### Post by markp1989 on 2010-01-20
> **Frak said:**
> I see absolutely no reason to use a low powered CPU alternative when all that is needed is to heavily underclock the current CPU when it's not in use.

every one in this thread gets the point, you dont see the use of this idea, but some people can, if every ones usage need/patern was the same there would only need to be 1 cpu/pc on the market!

heavily underclocking a high end cpu does save alot of power, but it will still use significantly more power then a cpu that was designed to be low power to begin with.

---

### Post by hwttdz on 2010-01-20
> **Frak said:**
> I see absolutely no reason to use a low powered CPU alternative when all that is needed is to heavily underclock the current CPU when it's not in use.

Well with a combination of underclocking and powering off cores one can achieve [(n-1)/n + 1 * (full speed core power - underclocked core power)/full speed core power ] * max power savings.  (where n is cores)

The only benefit of having asymmetric processors is that a single atom/low-power core is going to be lower power than a single i7/core2quad/whatever core.

---

### Post by Frak on 2010-01-20
> **markp1989 said:**
> every one in this thread gets the point, you dont see the use of this idea, but some people can, if every ones usage need/patern was the same there would only need to be 1 cpu/pc on the market!

heavily underclocking a high end cpu does save alot of power, but it will still use significantly more power then a cpu that was designed to be low power to begin with.
And a CPU that wasn't designed to use a lot of power will cause high amounts of latency to occur between jobs when the scheduler decides it needs to scale up for larger jobs.

---

### Post by lostinxlation on 2010-01-20
> **hwttdz said:**
> Why is there not a move towards asymmetric multi core/processor machines? let me explain what I mean. I have a machine that has a huge processor, which is sometimes terribly underutilized, and though the new intel chips can clock down cores and save power that way nothing compares to turning the cores off. So I'm wondering why there's no intel atom/intel core i7 board where the atom chip is powered up all the time, and the i7 chip is powered up as needed. I'm imagining that this would save on the order of 40-50 watts, which for a 24-7 machine could mean some pretty serious power savings and cost savings given that the secondary chip is super cheap to start with. One could also imagine this all happening on one chip where one core is anemic relative the others.
 
Nowadays, even ASIC chips have very fine clock gating control and what makes you think Intel is not doing that. 
Clock can be gated inside the core and so that clock does not toggle from certain points of clock trees. If you are feeding a clock to a chip, PLL inside the chip might be disabled, then there is no clock running inside the chip. For the logic signals, if no inputs signal toggles, no gates toggle which means no power consumption by logic gates. Of course, the big power eaters such as register files ALWAYS has some features to control power.
I haven't looked into the microarchitecture of these Intel chips, but I'm 99% sure they are doing something I mentioned above. .
 
Having said that, it might be a good idea not to provide the power to these chips not being used. Being designed by deep submicron process, the leakage through the transistors is no longer negligible, and in some occasion the leakage may waste more power than slowly running clocks. By shutting off the power supply, you can avoid such a waste of power.

---

### Post by hwttdz on 2010-01-22
Intel interestingly has already developed the ability to cut power to cores selectively.  I suppose it's just not implemented on desktop chips as a cost saving matter while producing.  

You can read about their "power gating" here
[http://arstechnica.com/hardware/news/2008/08/power-gating-and-turbo-mode-intel-talks-nehalem-at-idf.ars](http://arstechnica.com/hardware/news/2008/08/power-gating-and-turbo-mode-intel-talks-nehalem-at-idf.ars)
and of course somewhere on intel's site as well.  Which raises the question why is the power dissipation at idle (reported in the neighborhood of 80) of an i7 more than 25% of it's TDP (130, one might expect 33 watts if 3 cores are "off" and one is left running, and one would expect further savings from downclocking the remaining core).

(excuse my blatant bias towards intel and away from amd, I'm somewhat tied to the intel compilers which makes me somewhat tied to their chips and therefore I'm a bit out of the amd loop.  Though from what I understand intel is on the verge of introducing 32nm chips whereas amd is still at 45nm and a bit behind in other aspects as well)

---

### Post by lostinxlation on 2010-01-22
> **hwttdz said:**
>  Which raises the question why is the power dissipation at idle (reported in the neighborhood of 80) of an i7 more than 25% of it's TDP (130, one might expect 33 watts if 3 cores are "off" and one is left running, and one would expect further savings from downclocking the remaining core).
 

You can't cut off the power to the shared cache even though you disable 3 out of 4 cores and the shared cache accounts for like 1/3 of the entire die. The memory eats power, much more power than standard cells, and L3 cache is huge. So, disabling 3 out of 4 cores doesn't make the power consumption 1/4 of the full operation.

---

### Post by xir_ on 2010-01-22
qualcom chips do this, this is how they offer such great battery life. But then they are ARM.


i have a question about all this 686 786 and 986 stuff. Is this the same as the secure instruction set. I.e does i986=sse4.2

---

### Post by 3rdalbum on 2010-01-22
I had an opposite idea a while back, of having a beefy 3.6GHz single-core CPU and a 2.3GHz quad-core CPU on the same motherboard. When an intensive task only uses one thread, it gets allocated to the single-core CPU, and when a task can scale across multiple threads it gets allocated to the quad. This way you get good multiprocessing and good single-thread performance.

The i5 and i7 CPUs have the same advantage really (clocking a single core higher when only one core is in heavy use), and they'd be cheaper than a dual-CPU solution; but I thought my idea was pretty cool. I wonder if you could actually do this with a Skulltrail motherboard?

---

### Post by Skripka on 2010-01-22
> **hwttdz said:**
> Intel interestingly has already developed the ability to cut power to cores selectively.  I suppose it's just not implemented on desktop chips as a cost saving matter while producing.  

You can read about their "power gating" here
[http://arstechnica.com/hardware/news/2008/08/power-gating-and-turbo-mode-intel-talks-nehalem-at-idf.ars](http://arstechnica.com/hardware/news/2008/08/power-gating-and-turbo-mode-intel-talks-nehalem-at-idf.ars)
and of course somewhere on intel's site as well.  Which raises the question why is the power dissipation at idle (reported in the neighborhood of 80) of an i7 more than 25% of it's TDP (130, one might expect 33 watts if 3 cores are "off" and one is left running, and one would expect further savings from downclocking the remaining core).


It is simple really.

The CPU cores are not all that is on the CPU die.  i7 has the DDRs memory controller, and CPU cache on die, to name a few big ones-and they need juice.

Besides 130W is merely a measure of heat, and does not necessarily say anything about actual electrical consumption.

---

