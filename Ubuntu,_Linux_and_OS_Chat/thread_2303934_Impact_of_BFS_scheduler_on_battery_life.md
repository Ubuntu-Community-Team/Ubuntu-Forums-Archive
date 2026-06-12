---
title: "Impact of BFS scheduler on battery life ?"
date: 2015-11-22
forum: Ubuntu, Linux and OS Chat
---

### Post by blade4 on 2015-11-22
Hi all, 

Title pretty much says it all. I've found tons of stuff about potential performance benefits but next to nothing about impact on power consumption. On the one hand , greater throughput and performance through BFS seems to be based on more aggressive CPU usage  which would imply higher battery drain- on the other hand , BFS is touted as "simpler" and having to process less code definitely makes it easier on the battery.

Thoughts ?

---

### Post by tgalati4 on 2015-11-23
Years ago I read an article about a similar, aggressive CPU policy allows finishing a task quicker, which lowers power consumption.  At the time, it was justification for combining 10 servers running at 10% load (2,000 watts) into one server running 100% (250 watts).  When measuring my Dell PowerEdge 1750's they were 190 watts at idle and 240 watts at full load (2, dual-core Xeons, 2.8 GHz).  So scheduling policy becomes moot, you want to crank as fast as possible and avoid idle states because idle power is just heat generation with no work being done.  Servers from the 2006 era converted 99% of electrical power input into heat, regardless of workload.

So, looking at a laptop/notebook and now mobile devices, the same principles apply, except now you have a low-power processor and lower power use during idle, but now you have to juggle the extra power needed to wake and jump to higher C-states.  I would like to see some real data on [BFS]("http://https://en.wikipedia.org/wiki/Brain_****_Scheduler") on both older hardware and on newer hardware.

One can argue that a server scheduler and mobile phone scheduler should be different, but in Linux, they can be the same and they can be optimized for each workload.  Ultimately, saving power in the mobile space results in poor "hands-on" experience and responsiveness.  What ever happened to 400 ms on an Adroid phone?  When I click an app, it takes several seconds to respond.

The BFS manifesto:  [http://ck.kolivas.org/patches/bfs/bfs-faq.txt](http://ck.kolivas.org/patches/bfs/bfs-faq.txt)

---

