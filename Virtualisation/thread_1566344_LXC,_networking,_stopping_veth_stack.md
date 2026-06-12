---
title: "LXC, networking, stopping veth* stack"
date: 2010-09-02
forum: Virtualisation
---

### Post by leeezly on 2010-09-02
Hi there

I have lxc running on Lucid with Lucid guests. For networking I create a virtual network interface virnet0 (running bind) and specify "lxc.network.type = veth" and "lxc.network.link = virnet0" in the appropriate config file of the guests. Unfortunately, every time I start a guest system another network interface is created, named something like "veth*", which doesn't disappear when stopping the guest again.

Does anyone know how to stop, get rid of or not start in the first place this virtual network interface "veth*"? For lxc.network.type only veth seems to be resonable for me, since I need a private network.

Cheers

---

