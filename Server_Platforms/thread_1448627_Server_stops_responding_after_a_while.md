---
title: "Server stops responding after a while"
date: 2010-04-06
forum: Server Platforms
---

### Post by thestew42 on 2010-04-06
Okay so I recently decided to install Ubuntu and I went through all of the steps to set up a subversion server using svnserve. It all works except for one thing: it stops responding to remote computers after a while.

I have the server on a 4 port wireless router/switch in my dorm room. I set up port forwarding so that the server receives all traffic over the correct ports. The subversion server AND the default http server on Ubuntu work fine always as long as I access them from a computer connected to the switch in my room.

The problem is that if I try to access it from anywhere else, it won't respond at all unless it has been accessed by a computer on the switch recently (something like 30-60 minutes). So to fix it I have to go back to my room and access it from a computer on the switch. Then it will work from anywhere for another 30-60 minutes.

Any suggestions are appreciated.

---

### Post by KiLaHuRtZ on 2010-04-06
Sounds like an ARP issue.  What brand/type/model is your router?

---

### Post by thestew42 on 2010-04-06
It's a netgear. Pretty sure it's a WGR614.

---

