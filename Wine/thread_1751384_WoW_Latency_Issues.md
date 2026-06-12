---
title: "WoW Latency Issues"
date: 2011-05-06
forum: Wine
---

### Post by azunder on 2011-05-06
In the past few weeks my latency on wow has consistently remained between 2k-700ms, once or twice a day it will drop to 200ms for about 20 minutes before going back up again.

The setup I have to use is a bit awkward. I live in shared housing and the router is currently situated in a house next to ours (on the same land, kinda hard to explain). My computer is connected via ethernet to an access point that connects to the router via wireless. Whilst there are about 9 people living in both buildings only 4 people (myself included) actually use the internet. Unfortunately I can't move the router into my building or anything.

The thing is, in spite of the borked setup my connection seems fine, I download at 100kbs~ during peak times and upto 500kbs in the mornings and late evenings.

In spite of this, when running wow alone, my connection (both upload/download) ranges between 0.2-1.5kbs.

I can't tell if this is a problem with wine, wow or the fact that the access point has to pick up a signal passing through two brick walls.

Could anyone offer some insight into this, or if there are any ways I could optimize my connection other than setting up my desktop in the garden?

I'm running Ubunutu 10.04 and wine version 1.3.18

---

### Post by Tweak42 on 2011-05-08
Due to your wireless setup, your latency issue probably lie somewhere in the network stack, i.e. network drivers, wiring, cheap hardware, interference, or throttling by the ISP or at the router in the other building.  If wine was the problem, it should not vary by the time of day.

I would try asking in the network forum for tips on what tools/methods to use to try and isolate where the latency bottleneck is.  Definitely don't discount the quality of wireless hardware; I've seen quality G hardware out perform the latest gen N stuff.

---

### Post by cwwilson721 on 2011-05-08
Actually, wine really has nothing to do with latency issues. For example, when I run WoW in Win7 64bit, my lag is around double what it is in wine/WoW.

The lag is more than likely caused by wireless issues. Type of chip for your adapter, the type of router, and the route your data takes from there out to the servers can get very complicated.

Check yourself out in the Networking forums here at ubuntuforums.org, and if you still have an issue, come back here.

---

