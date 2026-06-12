---
title: "iptables cache loopback phenomena"
date: 2014-06-04
forum: Server Platforms
---

### Post by DeLol on 2014-06-04
Hey guys,

I had a strange phenomena this morning.
We have a route between two servers with a gateway in the middle.
For a moment had to take down the gateway for maintenance reasons,
so the route was down.
At this moment the first server send arp "who is" requests out and
looped back on his self, cached the looped route.
As we tocked the gw up again, the looped route rested in the local ip cache.
With an "ip tables flush cache" we could solve the problem.

How could this happen? And how can I make sure that this don't happen again?

---

