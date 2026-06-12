---
title: "network configuration"
date: 2006-10-14
forum: System76 Support
---

### Post by jhofmann on 2006-10-14
My System76 laptop was pre-loaded with Dapper.  It never seemed to have an "eth0", started life with eth1 and eth2 for the wired port and the wireless port.  The kernel randomly re-assigned eth1 and eth2, so I had to reconfigure networking using network manager almost every time I booted.    I could always make it work, but only after reconfiguring.

Well guess what:  There is a file named /etc/iftab that contained mappings from eth* devices to actual hardware by means of mac addresses.  This is all well documented, once I knew where to look.  The mappings did not, however, go with my machine.  I did not have that hardware in my machine.  I bet that hardware was in some poor, long-suffering developer's machine and something in the installation software failed to change that file to use the mac addresses in my machine.

I'm not completely satisfied with my changes and haven't tested it yet in a wireless situation, but it sure seems wrong to have mac addresses in /etc/iftab that aren't in the computer, so I'm following that up enthusiastically.

Comments?  Something else I should be doing?  This ever happen to anyone else?

Jim

---

### Post by crichell on 2006-10-14
This is something that has perplexed me for some time.  We noticed it when we were testing the Breezy > Dapper upgrade - the name of the interface bumped up on laptops and desktops.

We've been moving our laptops from the standard networking tool (System > Administration > Networking) to the new network-manager-gnome.  There is a bug that forced us not to use network-manager-gnome on two laptops (Pangolin Value & Serval) until the Edgy release.  With network-manager-gnome the name of the interface is irrelevant because available interfaces are assigned from HAL.

---

