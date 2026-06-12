---
title: "LXD container connect to LAN and internet but not host"
date: 2016-06-11
forum: Virtualisation
---

### Post by jay116 on 2016-06-11
I've searched and searched and cant seem to find a good answer. I've used the below guides to connect my LXD (LXC?) container to the LAN and I have been successful with that. with the below guide.

[https://insights.ubuntu.com/2015/11/10/converting-eth0-to-br0-and-getting-all-your-lxc-or-lxd-onto-your-lan/](https://insights.ubuntu.com/2015/11/10/converting-eth0-to-br0-and-getting-all-your-lxc-or-lxd-onto-your-lan/)

But now my Host, which has the correct LAN and subnet address cannot be seen on the LAN or connect to the internet. Can the Host and the Container use the same NIC to communicate on the network? My /etc/network/interfaces is setup just like the prior link accept my main eth0 is called enp2s0. when i do ifconfig I have a veth(.....) and a lxdbr0 as well. 

When searching for lxdbr0 I found the below site that explained a different way of creating a bridge using /etc/network/interfaces.d/eth0.cfg  (see below)

[https://insights.ubuntu.com/2016/04/07/lxd-networking-lxdbr0-explained/](https://insights.ubuntu.com/2016/04/07/lxd-networking-lxdbr0-explained/)

What is the difference in changing the interfaces file verse adding this file "eth0.cfg" inside the interfaces.d directory?

Any ideas on why my Host can no longer see the network?

---

### Post by jay116 on 2016-06-11
something to add... I decided to eliminate the lxdbr0 interface by setting /etc/default/lxd-bridge to:

**# Whether to setup a new bridge or use an existing one**
**USE_LXD_BRIDGE="false"**

**# Bridge name**
**# This is still used even if USE_LXD_BRIDGE is set to false**
**# set to an empty value to fully disable**
**LXD_BRIDGE=""**


this appears to have fixed the problem. I'm not sure if some how the host was confused by this addtional interface. Any thoughts?

---

### Post by MAFoElffen on 2016-06-16
The default installed lxdbr0 is a NAT, so not the same NID as the host, which gives an outside translated network ID to the outside world. I sually setup a bridge to my host netwrok nid to it's own nic FOR VM'S or containers on the host network, Then if they need to be on the host network, then I set those to that bridge.

You could also get a connect to your virtual network form your host, if you setup a route to that virtual Network ID (NID), via a second NIC, set to that NID as it's network. Or to setup a static route/hop.

A third way, that I've done, is to install a virtual router appliance to route between a virtual network and a bridge to the host network. Alternate to that is to set up macvlan or macvtap... but macvtap still sometimes has issues trying to talk directly to it's own physical host.

---

