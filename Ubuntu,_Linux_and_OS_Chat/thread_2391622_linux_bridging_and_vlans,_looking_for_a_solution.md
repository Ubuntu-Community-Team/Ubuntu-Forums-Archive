---
title: "linux bridging and vlans, looking for a solution"
date: 2018-05-11
forum: Ubuntu, Linux and OS Chat
---

### Post by syadnom on 2018-05-11
Ok, so I have a rather convoluted description here.

I am wanting to bridge the untagged vlan of ethernet ports and ignore 8021q tagged vlans on those ports.  example might be:

br0 (eth0, eth1)
eth0.10 is invisible to br0, no conflict 
eth1.10 is invisible to br0, no conflict

The reason being is that I want to run batman-adv mesh on the VLAN.  All the connected devices will not 'speak mesh' so I need the port's untagged traffic to work.  The mesh runs over VLANs happily (mtu adjusted appropriately of course).

so a system with 3 ethernet ports (PCEngines APU2C4 for example) might look like:

bat0 (eth0.10, eth1.10, eth2.10)
br0 (eth0, eth1, eth2, bat0)

Thoughts?

---

### Post by TheFu on 2018-05-11
Every LTS release has a slightly different method for these things, so always include which release you are running.  I can't help with the other stuff.  My APU2C4 runs pfSense and I don't use vlans.

---

