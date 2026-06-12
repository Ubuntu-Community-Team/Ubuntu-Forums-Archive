---
title: "LXC bridging chooses low mac address, causing connection issues"
date: 2013-05-24
forum: Virtualisation
---

### Post by martijntje on 2013-05-24
I am having some issues with my LXC containers. I have set them up to use a bridged device (in my case br0). The bridge device by default takes the mac address of the device it is paired to (bond0), which is fine.

However, when starting a container, the veth device that is linked uses a random mac address, which is sometimes lower than that of the bridge device, causing the bridge to change its mac address, which causes connections to be broken until the host sends out a packet and the arp table gets updated.

Is there anyway to force the mac address of the created veth device?

---

