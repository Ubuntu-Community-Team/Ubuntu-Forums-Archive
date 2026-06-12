---
title: "Program/Process Route to Specific Network Device"
date: 2010-07-30
forum: Server Platforms
---

### Post by johndoe32102002 on 2010-07-30
Is there a way to bind specific programs to specific network devices (not IPs, since I have dynamic IPs)?

For example, I wish for irssi to route through eth0 and w3m to route through eth1.  Keep in mind these devices have dynamic IPs, so I cannot attached them to an IP.

If anyone has the specific iptables code please post.  The solution cannot be accomplished through route since route pivots on IPs not devices.

---

### Post by juako on 2010-07-30
I think what you ask can be done with a combination of iptables + RPDB magic.

The iptables matching module that comes in handy is called "owner" and it matches packets based on the user id or group id of the process that owns the packet structure (that would roughly equal to "uid/gid who owns the packet").

You can force (by way of setuid, su or sudo) a process to run under specific credentials, and match packets originated by that process. That would be the first step.

The second step involves putting a mark on the matched packets, and use that mark to match again the packets in the Routing Policy DataBase.

The RPDB is checked before a packet is "routed" somewhere, and allows to look up a specific routing table according to the mark they have.

So, if you build several routing tables, each with a default route with the different network devices, and have the packets marked with, say a "1" lookup a routing table "gateway1", well, i hope you get the picture.

And all this post is only to draw "the picture". If you want to develop this solution, i'll be glad to help you do with it.

Cheers :D

---

