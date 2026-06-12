---
title: "SunFire V20Z bogging down"
date: 2012-07-06
forum: Server Platforms
---

### Post by SylenThunder on 2012-07-06
OK, at this point I'm not even sure whether it's the server, or the OS, but since I can't find any info, I'm going down both paths to see if anyone knows anything. Google searches are netting very little information I'm afraid.

**The Setup**
I have a SunFire V20z with two 78GB Hard drives running in RAID, and 16GB of ram. (Max for the device.)
I am running Ubuntu 10.04 LTS 64-bit on the server. It's a pretty basic install, and I haven't added a lot of software to it aside from what I need to run the server system.

**The Problem**
As soon as RAM gets over about 10.5-11GB used, the server gets very slow to respond. I haven't had this happen on any other systems with this setup, which makes me think that it's something with the hardware configuration.
I've tested the RAM and it all checks out fine.
Temperatures are nominal so I can rule out overheating I think.

If I kill processes and get the RAM usage back down to the 10GB area, then the server begins responding quickly again. This is very frustrating because I've run other servers up to about 90% of RAM usage without having any kind of delay like I'm experiencing here.

I would also like to note that CPU load is relatively low, and the Hard drive is not being accessed much either. Simple commands like a file list can take 3-5 times longer to run depending on how much RAM over the 11GB mark is used.

Edit: It was suggested to me that I should increase the swap size, even though it's not being used, so I created a 16GB swap file and enabled it. Unfortunately that did nothing to resolve the issue.

---

