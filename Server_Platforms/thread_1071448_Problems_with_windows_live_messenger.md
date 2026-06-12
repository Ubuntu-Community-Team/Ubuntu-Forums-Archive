---
title: "Problems with windows live messenger"
date: 2009-02-16
forum: Server Platforms
---

### Post by fragtion on 2009-02-16
I'm running a server pc with 1 NIC (eth0 - static 172.16.6.1/27) which also has two active pppoe sessions for the internet - ppp0 and ppp1, both with DNAT MASQUERADE so that clients on the network can access the internet using 172.16.6.1 as the gateway IP. ppp0 is the default gateway, and ppp1 only has some specified internet routes. IPv4 forwarding is enabled.
However, when using this gw setup I can't sign into msn/windows live messenger on my windows machine. It signs in if I dial up on the windows machine directly, or use a linksys wrt54g router instead of the linux server. Everything else seems to work fine, but not MSN messenger ?! ;/
Someone suggested upnpd to me, but the problem is how do I get upnpd to work with multiple external interfaces? I doubt that's the problem anyway... I tried 'upnpd eth0 ppp0' which didn't make any difference.
Any suggestions would be appreciated =]

---

