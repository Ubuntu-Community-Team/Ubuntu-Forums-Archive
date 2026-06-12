---
title: "Extreme Leopard or .... for simulations and parallel computing with lots of data"
date: 2014-03-30
forum: System76 Support
---

### Post by flucoe2 on 2014-03-30
Hi,

In a couple of months I'll have funding to buy a powerful desktop, that I'll use to solve optimization problems that involve parallel computing with simulations and huge datasets, probably using MATLAB. Until today I have been very happy with my Pangolin Performance for work with smaller datasets (or before running the code in a cluster), so I was thinking on buying an Extreme Leopard with all the RAM available (64GB), one of the two processors with six cores, and a GPU. However, I have tons of questions. 

First, has anybody tried the new Extreme Leopard for this kind of work? If so, can you say something about your experience? 

Second, how likely is that I'll perceive the difference between i7-1930k and the i7-4960x processors? For parallel applications I would benefit from more cores but I don't know how I would benefit from the the i7-4960x relative to the i7-1930k given that they have the same number of cores.

Third, any recommendation on graphic cards? Using the GPU for parallel computing is something new to me, but I'm looking forward to learning it. However, I have no idea what would be a good option and what would be an overkill. 

Finally, though I have done some research trying to understand the benefits of RAID storage options, I don't know whether I would actually benefit from something like this, or if it is meant for someone who plans to do something different with the desktop. 

By the way, right now my alternative is to buy something as a gaming desktop and use it for my work. Do you have any suggestions/experience?

Thank you,

---

### Post by slooksterpsv on 2014-03-30
I'd choose the 4960 if you're running larger dataset applications, the boost in cache will really help. Noticeable? It varies depending on the code itself because depending on how well the code is optimized the 4930 may perform better, so it really depends on if the code will use the full extent of the CPU.

GPU is very useful in parallel computing if it's implemented to be used, again depending on the code, it may or may not work.

Lets see you said MATLAB? If that's the app- the most and highest you can get looks like it would be the best, although I wouldn't gt the overclocked 2880 CUDA Cores NVidia card.

#4 - How large of datasets are we talking? Are you going to constantly be reading and writing large quantities of data? If so the hard drive could present an issue of not being able to keep up and may have to wait. RAID works in a variety of ways:
RAID 0 splits the data up between 2 drives which makes it faster e.g.
HDD 1 reads and writes at 50MBs
HDD 2 reads and writes at 50MBs
If you RAID 0 those together, you can get a theoretical read/write of 100MBs.
SSD 1 reads and writes at 400MBs
SSD 2 reads and writes at 380MBs
If you raid 0 those together, you can get a theoretical read/write of 760MBs

Now if you're concerned about data loss; RAID 1 copies the same data to each drive
RAID 1 drives
HDD 1 has file xyz.zip
HDD 2 now has file xyz.zip

[http://en.wikipedia.org/wiki/Standard_RAID_levels](http://en.wikipedia.org/wiki/Standard_RAID_levels) - has better information on RAIDs.

A gaming desktop? You could do that, but if you did that it'd be better to build it yourself. You could end up saving money overall and get better components. If it was a prefab gaming desktop, performance would vary depending on the hardware. I'm wondering if MATLAB would work better with like the Workstation Graphics like the AMD FirePro cards or the Nvidia Quatro cards...

---

### Post by flucoe2 on 2014-03-31
Thank you! I really appreciate your feedback.

---

