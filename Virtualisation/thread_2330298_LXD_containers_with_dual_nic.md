---
title: "LXD containers with dual nic"
date: 2016-07-10
forum: Virtualisation
---

### Post by gcesab on 2016-07-10
Hi all,
I'm trying to configure a LXD container with two nics but the second one cannot reach the external network. Here is my config:

/etc/network/interfaces


 auto ens160
iface ens160 inet manual


 auto br0
iface br0 inet static
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.1
bridge-ifaces ens160
bridge-ports ens160
up ifconfig ens160 up


 auto ens192
iface ens192 inet manual

 
auto br1
iface br1 inet static
address 10.10.0.103
netmask 255.255.255.0
bridge-ifaces ens192
bridge-ports ens192
bridge-stp on
up ifconfig ens192 up

Default profile is:

devices:
  eth0:
    name: eth0
    nictype: bridged
    parent: br0
    type: nic
eth1:
    name: eth1
    nictype: bridged
    parent: br1
    type: nic

Both IP addresses are statically configured in the container, the first in the 192.168.1.0 subnet and the second in the 10.10.0.0 subnet. The first nic works well, I can ssh from external network. The second one can ping only the LXD host address and viceversa. The LXD host address can ping everyone on the 10.10.0.0 network.

What's wrong in my config? Any suggestion?

---

### Post by MAFoElffen on 2016-07-10
I'm assuming that interfaces file is on the Host right?

What I see is that both your physical ports (eth0 & eth1) are set to manual. Then you setup your bridges.  But when you setup your bridges, you did not bind them to a physical port, so they aare logically disconnected to anything.

Before I tell you what the specific fix is...
Could you confirm that this is on the Host?
Did you disable the LXD default bridge? brlx1?
What is your host's local network ID?
Do you have 2 or three nics on the host? 

The reason I ask the last 3 is that I think your br1 is going to confilct with brlx1... and if you do not have 3 NIC's your 2 bridges set up that way would disconnect your host from the outside world and make it un-reachable.

Could you post the results of 
```

ifconfig -a

```

---

