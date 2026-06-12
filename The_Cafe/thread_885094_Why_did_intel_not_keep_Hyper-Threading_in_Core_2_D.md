---
title: "Why did intel not keep Hyper-Threading in Core 2 Duos and Pentium Dual Core?"
date: 2008-08-09
forum: The Cafe
---

### Post by Lord Xeb on 2008-08-09
Just curious.

---

### Post by zachtib on 2008-08-09
> **Lord Xeb said:**
> Just curious.

well, the Core CPUs were derived from the Pentium 3/m, which didn't have HT... HT made a return in the Atom, however, and will also be in Nehalem.

---

### Post by MaxIBoy on 2008-08-09
That explains why some games detect my laptop's core 2 duo as a pentium 3.

---

### Post by blastus on 2008-08-10
> **Lord Xeb said:**
> Just curious.

Because multiple cores are way more efficient than hyper-threading. Hyper-threading was introduced back in the days when Intel hit the 4Ghz barrier.

---

### Post by Dremora on 2008-08-10
Because Hyperthreading serves no real purpose in a well designed CPU.

The massive performance gains it gave the Pentium 4 were more indicitive of how many clock cycles the Pentium 4 wasted than how good HT was. (It isn't)

---

### Post by ghindo on 2008-08-10
What *is* hyperthreading?

---

### Post by LaRoza on 2008-08-10
> **ghindo said:**
> What *is* hyperthreading?

[http://en.wikipedia.org/wiki/Hyper-threading](http://en.wikipedia.org/wiki/Hyper-threading)

---

### Post by Dremora on 2008-08-10
> **ghindo said:**
> What *is* hyperthreading?

The processor essentially fakes a non-existent second core so that it can take advantage of wasted execution time (Netburst Pentium 4's had abundant CPU wastage) in ordeer to run a second thread.

On a Pentium 4, this made for a chip that was 10-15% faster usually.

On a Core 2 CPU core, maybe 1-3% at best, were it implemented, sometimes it would even lose you that much.

It's really a stupid idea and was a hack to make the Netburst not suck as bad.

Intel mainly just wants advertising material that says Nehelam will run 16 threads on an 8 core chip, which will technically be true, yet mean little, at the same time.

---

### Post by Canis familiaris on 2008-08-10
Because HyperThreading has far many disadvantages.

And I am sure Intel are making a big mistake by re-introducing HT in Nehalem.

---

### Post by zachtib on 2008-08-11
> **Anurag_panda said:**
> Because HyperThreading has far many disadvantages.

And I am sure Intel are making a big mistake by re-introducing HT in Nehalem.

not necessarily. Other CPUs are moving towards multiple threads per core (I believe the new Power CPUs are, for example) And if done right, I think HT can be a good thing.

---

### Post by LittleLORDevil on 2008-08-11
> **MaxIBoy said:**
> That explains why some games detect my laptop's core 2 duo as a pentium 3.

Because it is the same architecture, just two of them.

---

### Post by Canis familiaris on 2008-08-11
> **LittleLORDevil said:**
> Because it is the same architecture, just two of them.

It was based on the Pentium III architecture in a crude sense. But it is not just two Pentium III cores.

---

### Post by oldsoundguy on 2008-08-11
add to the above the fact that a Hyperthreader runs HOT .. not warm but HOT.  They become whole house heaters.  I ran a 3.06 and it ran at 70c.  It would heat my place in the winter!  AND the cost of running the AIR CONDITIONING most of the rest of the year to keep the room livable.
That heat shortened the life of the motherboard by doing some damage to the capacitors on the power rails!

---

### Post by Dremora on 2008-08-12
All Netburst CPUs are hotter than hell, it's because Intel was basically overclocking them to make up for the fact that their execution pipeline was so wasteful, it's called the Ghz Myth.

Anyway, look at a heatsink for an Athlon64 3200+ (2.2 Ghz) and a heatsink for a Pentium 4 Extreme Edition at 3.8 Ghz (basically the same performance), you'll see that the Pentium 4 heatsink is nearly twice the size.

The good part about this is they had plenty of heatsinks that were as big as a Buick leftover after Netburst died off, so I looked at my Core 2 Duo and they decided to use a Pentium 4's heatsink on it, needless to say it runs pretty damned cool, it practically begs me to overclock it, I hear it calling in my dreams. :lolflag:

---

### Post by Lord Xeb on 2008-08-13
You should. It will cool your core all the way to about 3-3.2 GHz with no problem. For once, i actually like the default heatsink. It is a good one. >_>

---

### Post by BlueSkyNIS on 2008-08-13
> **oldsoundguy said:**
> add to the above the fact that a Hyperthreader runs HOT .. not warm but HOT.  They become whole house heaters.  I ran a 3.06 and it ran at 70c.  It would heat my place in the winter!  AND the cost of running the AIR CONDITIONING most of the rest of the year to keep the room livable.
That heat shortened the life of the motherboard by doing some damage to the capacitors on the power rails!

I must say I am one of the lucky ones because I have pretty cool Prescott (in P4 levels) and would not call it that HOT! My P4 531 (3GHz, 84W TDP) is between 35+ (idle) and 50 *C (load), and it's summer here (30+ *C) ;)

P.S. How can I check temps in Ubuntu? :)

---

### Post by oldsoundguy on 2008-08-13
not tried this .. ymmv on it:

[http://www.quietearth.us/articles/2006/09/30/Ubuntu-Sensor-temperature-monitoring-with-lmsensors](http://www.quietearth.us/articles/2006/09/30/Ubuntu-Sensor-temperature-monitoring-with-lmsensors)

---

### Post by BlueSkyNIS on 2008-08-13
> **oldsoundguy said:**
> not tried this .. ymmv on it:

[http://www.quietearth.us/articles/2006/09/30/Ubuntu-Sensor-temperature-monitoring-with-lmsensors](http://www.quietearth.us/articles/2006/09/30/Ubuntu-Sensor-temperature-monitoring-with-lmsensors)

Thanks, my 531 is idling at 31 *C :) :popcorn:

---

### Post by Canis familiaris on 2008-08-13
> **BlueSkyNIS said:**
> Thanks, my 531 is idling at 31 *C :) :popcorn:

Mainly because of CPU Frequency scaling using SpeedStep it it running cool. Netburst based CPUs will run hot if put into prolonged stress (all CPUs for that matter but particularly Netburst based ones)

Isn't CPU Freq. Scaling Great. :D

[http://en.wikipedia.org/wiki/Dynamic_frequency_scaling](http://en.wikipedia.org/wiki/Dynamic_frequency_scaling)

---

### Post by Lord Xeb on 2008-08-14
My Pentium M (on my lappy) likes to get hot sometimes depending on what I am doing. It gernerally hovers around 120F during idle and about 172-178 when under prolonged stress (like when I use my pSX emulator or whatnot)

---

