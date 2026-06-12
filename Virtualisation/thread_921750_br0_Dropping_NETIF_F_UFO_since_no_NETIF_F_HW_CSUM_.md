---
title: "br0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature."
date: 2008-09-16
forum: Virtualisation
---

### Post by Jordanwb on 2008-09-16
I set up VirtualBox to support networking inside guest OSes. I set up a bridge like the Community how-to said, with the virtual interface and eth0. When I boot up Ubuntu (Host OS) I get this message:

> br0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.

/etc/network/interfaces:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto etho
iface eth0 inet manual

auto br0
iface br0 inet static
	address 192.168.1.4
	netmask 255.255.255.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	bridge_ports eth0 vbox0

```

---

### Post by mrsteveman1 on 2008-09-16
I believe this has to do with offloading checksums to the hardware, and there is no real hardware to offload to with a virtual interface.

Is it working though? Does networking seem to function correctly?

---

### Post by Jordanwb on 2008-09-16
Yeah everything works just fine, it's just that configuring the bridge takes several seconds and I thought that there might be a problem.

---

### Post by gyterpena on 2008-09-17
I have same message in my logs and network is not working fine. I'm still testing it but quite often hosts won't get ip assigned from DHCP until I do network restart on box all I'm getting from /var/log/messages and syslog is this 
br0: port 2(eth2) entering learning state
br0: topology change detected, propagating
br0: port 2(eth2) entering forwarding state
br0: port 4(eth4) entering learning state
br0: topology change detected, propagating
br0: port 4(eth4) entering forwarding state
br0: port 1(eth1) entering learning state
br0: port 3(eth3) entering learning state
br0: port 3(eth3) entering disabled state
br0: port 3(eth3) entering learning state
br0: topology change detected, propagating
br0: port 1(eth1) entering forwarding state
br0: port 3(eth3) entering disabled state
br0: port 1(eth1) entering disabled state
br0: port 4(eth4) entering disabled state
br0: port 4(eth4) entering learning state
br0: topology change detected, propagating
br0: port 4(eth4) entering forwarding state

---

### Post by epicac on 2008-09-30
I have the same message in my logs and my network is not working. I've set up an bridge in /etc/network/interfaces to make a bridge. I trying to setup network to use libvirt/kvm/virsh, but can't connect or ping the virtual machines.

auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 192.168.0.30
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.6
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

---

### Post by thegreatpretender on 2008-09-30
Same problem here! 

After changing networking to bridging for VirtualBox the network connection to my router is sometimes not established correctly. Sometimes it works and sometimes not. If I restart my machine it usually works...

During startup I get this in the log: 
> br0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM

However, networking seems to be established to some extent as an IP-address is given to the br0 interface.

If I restart the network manually it works:
```

la@anteca:~$ sudo /etc/init.d/network restart 

```

My network config:

```

la@anteca:~$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# Bridge for Host interface for VirtualBox
auto br0
iface br0 inet dhcp
    bridge_ports eth0

```

I am running Ubuntu Studio 8.04 with all updates and VirtualBox 2.0. Had the same problem before with VirtualBox 1.6.

Happy if someone can help out!

---

### Post by Jordanwb on 2008-09-30
For me what I did was set the Virtual Machine to use NAT.

---

### Post by gyterpena on 2008-10-01
More information here specially last paragraph.

[https://bugs.launchpad.net/ubuntu/+source/bridge-utils/+bug/274298]("https://bugs.launchpad.net/ubuntu/+source/bridge-utils/+bug/274298")

---

