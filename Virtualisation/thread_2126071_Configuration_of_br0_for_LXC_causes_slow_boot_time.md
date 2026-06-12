---
title: "Configuration of br0 for LXC causes slow boot times"
date: 2013-03-15
forum: Virtualisation
---

### Post by zoarre on 2013-03-15
Hi all,

I've configured a network bridge so that I can access LXC containers from the LAN.

I was unable to find instructions specific for LXC (lxcbr0 seems to be NAT, not bridged), so I adapted the instructions for KVM found here:

[https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)

My /etc/network/interface looks as follows:

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet manual

auto br0
iface br0 inet dhcp
   bridge_ports eth1
   bridge_stp off
   bridge_fd 0
   bridge_maxwait 0
```

The good news is that everything appears to work fine. The bad news is that since I've installed the bridge, the startup screen reports that it was unable to bring the network up completely after waiting for a long period of time.

I have a couple of network drives in my /etc/fstab file. I've disabled them and it doesn't appear to affect anything. 

Any idea what I can do to eliminate the startup problem?

Regards,
zoarre

---

