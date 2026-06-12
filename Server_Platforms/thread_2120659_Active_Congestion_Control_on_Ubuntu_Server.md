---
title: "Active Congestion Control on Ubuntu Server"
date: 2013-02-27
forum: Server Platforms
---

### Post by Pimentel on 2013-02-27
Hy everyone!

I'm looking for an Active Congestion Control method for Ubuntu Server, but none of the congestion avoidance algorithms in the linux Kernel I'm aware of seem to do the trick.

This would be similar to Gargoyle Router's implementation, which I assume is done in userspace: It constantly checks the latency to a host (generally the WAN default gateway) and adjusts throughput limit to prevent delay from increasing regardless of the load, which plays a huge factor in latency/jitter constrained services. Please check image attached for more on this.

I've been successfully using this in routers for awhile, but I'm now looking forward bringing this kind of control closer to the server's interfaces.

Any suggestions?

Thank you very much! ;)

---

