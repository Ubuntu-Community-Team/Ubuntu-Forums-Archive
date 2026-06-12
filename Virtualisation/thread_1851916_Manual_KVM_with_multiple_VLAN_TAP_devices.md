---
title: "Manual KVM with multiple VLAN TAP devices"
date: 2011-09-29
forum: Virtualisation
---

### Post by rauxon on 2011-09-29
I'm manually creating KVM guests, and the tap devices that are being created seem to pick up a massive amount of data I wouldn't expect them to.

Server configuration is that I have 6 bridges.  There are 2 physical NICs, and 3 VLANs running on each.  I've created a bridge for each "combination".

At this point I then create the guest, with 6 NICs - one attached to each bridge.  And this is where the problems start. The NICs appear to see the untagged VLAN traffic from eth0 even though that's not attached to the bridge.

Running a tcpdump against the TAP interface (or either of the physical interfaces) shows all the traffic, but running it against the bridge shows nothing.  carrying out an ifconfig <name> down against the bridge doesn't stop it either.

I can, and will if it helps, attach the scripts I'm using to test - but has anyone else experienced this and can tell me what I'm doing that's stupid?

I'm trying to setup a lab so that I can run an Oracle RAC with something approaching a configuration that matches (to the guest) a production system - so that the DBAs can learn how to use RAC...

Don't ask. :)

---

