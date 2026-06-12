---
title: "Link bonding and VMWare Server bridged mode"
date: 2009-08-26
forum: Virtualisation
---

### Post by batfastad on 2009-08-26
Hi everyone

We've recently upgraded to a Netgear L2 managed gigabit switch which supports link aggregation. I've just read through the Virtualisation mega-thread and it seems VMWare Server is probably the best option (I'm thinking ease of setup here).
Also bridge mode networking seems to be what I need as I want the VMs to get their IP addresses from our IPCop DHCP server and for them to be accessible from the internet.

I know it's possible to combine 2 gigabit NICs on the server into a single bonded link... mode 4 802.3ad link aggregation with LACP per this wiki article [https://wiki.ubuntu.com/LinkAggregation](https://wiki.ubuntu.com/LinkAggregation)
I almost got this working with our old smart switch until I realised the switch didn't support LACP so it didn't quite work.

But is it possible to combine this with bridged networking under VMWare Server?
So there's 1 2 physical links bonded together, but each VMWare guest has its own DHCP IP address over this bonded link.

Anyone know if this is possible?

The reason I ask is that now all our users are connected via gigabit to the switch, and the server is connected via gigabit... there's a higher chance of the server link being swamped by traffic if a few users start transferring large files to/from the server.
Previously the server was connected gigabit and users at 100mb so the chance of that happening was much lower.
With mode 4 link aggregation that should give us a theoretical link speed of 2Gbps.

EDIT: also I guess the host will also need to get an IP address for the VMWare Server web management interface. So that's 3 static IP addresses by DHCP over a bonded link.
Is this possible?

Cheers, B

---

