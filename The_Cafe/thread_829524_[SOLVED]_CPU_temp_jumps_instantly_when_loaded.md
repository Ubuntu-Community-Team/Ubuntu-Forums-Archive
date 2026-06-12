---
title: "[SOLVED] CPU temp jumps instantly when loaded"
date: 2008-06-14
forum: The Cafe
---

### Post by chapterthree on 2008-06-14
Hi All,

I'm not quite sure where I should go with this question, but the Ubuntu community is a great place to start. :)

I recently upgraded my rid, Gigabyte GA-EP35-DS3P motherboard, Intel E8400 Core 2 Duo 3.0GHz processor, and 2x2GB DDR2 Corsair Dominator memory.  Right now I just have the stock OEM heatsink and fan that came with the boxes processor.  The plan was to get an aftermarket replacement, but based on reviews I read the OEM setup seemed to hold it's own, even under OC.

The system is currently running at vanilla stock levels, no OC on any component (mainly because I can't).  When the system is put under a decent load, the CPU temperature jumps instantly, but then levels off at a stable temperature, and instantly drops when the load is removed.  (I am using the 'stress' program to load the system)

In the image I left stress running for about 20 minutes, then did 2 more tests, a timed 2 minute run, and a timed 1 minute run (the 2nd and 3rd spikes in the graphs).

Does anybody have a comparable rig?  Is this normal?  My main concern is that the heatsink isn't fully seated on the CPU, or the bond isn't complete.  The OEM heatsink does come with thermal grease pre-applied, and the instructions didn't mention that additional grease was needed (nor did anybody in any of the reviews I read) so I figured all should be well.

But if the bond wasn't great, I would expect to see the temperature to fluctuate or gradually rise over time.  Because the temp seems to remain very stable at load, I think the heatsink is doing it's job and the connection is good.  Maybe this is just how Core 2 Duo's are?  In reality I think a 20-minute load temp of just under 60C is acceptable for the OEM setup (and ambient in the room is about 25C).

Maybe I'm worrying about nothing?  :)

---

### Post by bufsabre666 on 2008-06-14
yes worrying for nothing, thats what load means, youre cpu is more active, and if you have scaling enabled when not under load it might be well downclocked so when load hits its natural for more heat, besides it looks like it peaked at 57-58ish, thats not high enough to trigger an auto shutdown

---

### Post by chapterthree on 2008-06-14
I guess the main thing was how suddenly the temperature jumps.  I don't recall my previous setup (P4 3.0GHz OEM heatsink) insta-jumping immediately on load, it would gradually increase and level off.  But of course that's like apples and oranges, which is why I was thinking maybe the instant jump is normal for the Core series processors.

---

### Post by information_entropy on 2008-06-14
My Core 2 will go from 34c to 54c in ten seconds if I start a graphic
intensive game in Wine.

The first time that happened, I took the heat sink off to make
sure I had not forgotten to put heat sink compound on, or done
something else equally stupid.

Apparently the Core 2 can really heat up fast.

---

### Post by chapterthree on 2008-06-14
OK perfect, sounds like it is expected behavior with the Core 2 procs.  I was hoping to get comfirmation from somebody else before I did the same think (pull the proc, re-apply grease, etc).

Thanks!

---

### Post by kripkenstein on 2008-06-19
Hi, on a related note, I have a new Core 2 Duo, and it always runs at 3 GHz - frequency scaling seems to not work. Cpufreq-info gives me
```

$ cpufreq-info 
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU

```
Is this normal? I thought modern CPUs changed their frequencies to save power...

---

