---
title: "internal and external networks on separate interfaces, but on same net"
date: 2010-06-01
forum: Server Platforms
---

### Post by MSalivar on 2010-06-01
I'm trying to figure out if there are going to be any pitfalls.  And if so, if I can work around them, or just skip this idea of a separate interface for WAN.

We don't have a budget for multiple servers.  I really wish we did, but we don't, and if we did, it would likely be a backup server and wouldn't help me here.

I'm going to have three interfaces, two gig-e adapters bonded using 802.3ad for the sake of speed (now bond0), and a 100Mb card for external access (now eth2).  The router is set to static 1:1 NAT for eth2's IP.  Furthermore, bond0's IP is excluded from the overloaded NAT pool.  However, both interfaces have IP's on the same network (and subnet.)

tl;dr: I have two interfaces, bond0 is internal only, eth2 has access to the WAN, but is still on the same local network.

This server is going to be a bit of a jack of all trades.  BIND is going to both cache, and be the master of domain.local.  FTP is going to allow both anonymous connections from the WAN, and internal connections from network document scanners. Samba is going to be internal only, as will DHCP.  I'll need to be able to SSH in from outside, and I'm also considering OpenVPN.

Obviously I want to set a static route to make eth2 the default route.  That should take care of everything going to the WAN, including BIND recursions, correct?

Then, obviously I don't want anything intended for the internal network going out eth2, simply because it's slow, and also because it's going to be heavily firewalled (eth2's entire reason for existence.)  I figure everything should just send back out on the interface it received on, but I'm not confident of that.  If I set a static route for the internal network out bond0, will that take precedence over directly connected networks with GNU/Linux routing behavior?  Heck, can I even have two interfaces on the same network?  As I think about how Cisco routing behavior would behave in this situation, I realize it wouldn't even let me set the second interface.

Note: I do NOT want this machine to route between bond0 and eth2.

Note 2: Our IP block isn't routed to us, so I can't subnet it. I'm not sure of a way to get one of our public IP's directly to the machine, because our router only physically routes between the WAN port and a single configurable VLAN assigned to its internal 4 port switch.  I might be able to setup a DMZ, but that's way above me at this point. I suppose I could plug eth2 into the DSL modem which is setup as a transparent bridge, but I'd rather not bypass the router's firewall.

---

