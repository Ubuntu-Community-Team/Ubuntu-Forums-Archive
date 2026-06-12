---
title: "Internet Usage Monitoring"
date: 2008-08-22
forum: Server Platforms
---

### Post by lordmontie on 2008-08-22
I'm looking for a solution to monitor / log internet usage on a LAN. I've tried many solution and so far the best that I've found is ntop. I would like to have an ubuntu server connected to a port that's mirroring another on my core switch and monitor / log all network traffic. Ntop does this very well, but I'm still looking for a little more. I need to log website usage and keep the history.

The company had used [http://www.lightspeedsystems.com/](http://www.lightspeedsystems.com/) for their firewall, web filtering, spam blocking, and logging system. We had replaced it with a CheckPoint Firewall, MessageLab spam filtering, and now need something for web / internet usage monitoring. We are not worried about blocking content but just want to log it.

Ideally the solution would be passive as to not add an additional box in the path outbound for another point of failure. Does anybody recommend anything else? Thanks!

---

### Post by windependence on 2008-08-22
Untangle, pfsense, or m0n0wall.

-Tim

---

### Post by Yuki_Nagato on 2008-08-22
These guys may have a solution:

_[http://www.opendns.com/]("http://www.opendns.com/")_

---

### Post by wirepuller134 on 2008-08-22
We still use are isa server, so we use GFI web monitor.

---

### Post by lordmontie on 2008-08-25
Thanks all. I looked into opendns.com but the logs don't show the detail I need. They do provide a wonderful content filtering that looks promising. 

pfsense and m0n0wall looks to be mainly a firewall / router. Untangle on the other hand looks more likely. The only issue is that I don't see any traffic monitoring that will show both allowed and blocked traffic. I've only found the blocked reports ...

Once again, I'm looking for a passive solution that will log all network traffic and keep detailed info about each host's traffic with HTTP / HTTPS details. Thanks!

---

### Post by sukhhari on 2008-10-14
If you find any solution? please help me out at [email]sukhhari@yahoo.com[/email]

Harish:lolflag:

---

