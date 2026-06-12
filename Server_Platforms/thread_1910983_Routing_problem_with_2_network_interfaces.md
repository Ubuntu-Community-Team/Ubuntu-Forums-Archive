---
title: "Routing problem with 2 network interfaces"
date: 2012-01-18
forum: Server Platforms
---

### Post by luismpedro on 2012-01-18
Dear all, 
   I've a base (physical) machine with two network interfaces. This machine hosts two virtual machines. From one of the virtual machines I have no problems with network access. With the second one, I have no network access. I think the problem is in the base machine routing configuration.
   Here is the configuration of each one of the machines:

**Base machine: 192.168.3.4**
*/etc/network/interfaces*
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.3.4
	netmask 255.255.255.0
	network 192.168.3.0
	broadcast 192.168.3.255
	gateway 192.168.3.9
	# dns-* options are implemented by the resolvconf package, if installed


# The DMZ network interface
auto eth1
iface eth1 inet static
        address 192.168.2.12
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
        # dns-* options are implemented by the resolvconf package, if installed

```
*route -n*
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.37.131.0     0.0.0.0         255.255.255.0   U     0      0        0 vnic1
10.37.130.0     0.0.0.0         255.255.255.0   U     0      0        0 vnic0
192.168.3.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.3.9     0.0.0.0         UG    100    0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth1

```

*ip route show*
```

10.37.131.0/24 dev vnic1  proto kernel  scope link  src 10.37.131.2 
10.37.130.0/24 dev vnic0  proto kernel  scope link  src 10.37.130.2 
192.168.3.0/24 dev eth0  proto kernel  scope link  src 192.168.3.4 
192.168.2.0/24 dev eth1  proto kernel  scope link  src 192.168.2.12 
192.168.122.0/24 dev virbr0  proto kernel  scope link  src 192.168.122.1 
169.254.0.0/16 dev eth1  scope link  metric 1000 
default via 192.168.3.9 dev eth0  metric 100 
default via 192.168.2.1 dev eth1  metric 100 

```

**Virtual server 1 (192.168.3.4)** (this one works perfectly)
*/etc/network/interfaces*
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.3.3
	netmask 255.255.255.0
	network 192.168.3.0
	broadcast 192.168.3.255
	gateway 192.168.3.9

```
*route -n*
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.3.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.3.9     0.0.0.0         UG    0      0        0 eth0

```

*ip route show*
```

192.168.3.0/24 dev eth0  proto kernel  scope link  src 192.168.3.3 
default via 192.168.3.9 dev eth0  metric 100 

```


**Virtual server 2 (192.168.2.15)** (the one network **doesn't work**)
*/etc/network/interfaces*
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.2.15
	netmask 255.255.255.0
	network 192.168.2.0
	broadcast 192.168.2.255
	gateway 192.168.2.1

```
*route -n*
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

```

*ip route show*
```

192.168.2.0/24 dev eth0  proto kernel  scope link  src 192.168.2.15 
default via 192.168.2.1 dev eth0  metric 100 

```

Any idea about what is wrong and how to solve it?

Thank you very, very much in advance,

Kind regards,

Luis

---

### Post by Savio2010 on 2012-01-18
your first vm is in the network
network 192.168.3.0

The second one in the
network 192.168.2.0

Try putting both in the VMs in network 192.168.3.0

or else you need to access the second vm from your dmz network.

---

### Post by luismpedro on 2012-01-18
> **Savio2010 said:**
> your first vm is in the network
network 192.168.3.0

The second one in the
network 192.168.2.0

Try putting both in the VMs in network 192.168.3.0

or else you need to access the second vm from your dmz network.

Thanks for the answer, but I really need the second VM to be in 192.168.2.0. It's a requirement for this configuration. 

LP

---

### Post by HugoSerrano on 2012-01-18
Hello! 
What virtualization system are you using?

My guess it's that your second Virtual Machine it's virtualizating the NIC in the eth0 of the base host.

---

### Post by Savio2010 on 2012-01-18
Which VM platform are you using Virtual Box, VMware?

Any way
Since you are using vm change to second vm configuration to use 2 network cards, and set one network card in the 2.x network and the other in the 3.x network. I don't know if this may raise security issues.

The only way round is to access the second vm from the
DMZ network / 192.168.2.x

---

### Post by Charlietje on 2012-01-18
Hello,

from your configuration you have 2 default gateways. There can only be one "default"
```
0.0.0.0         192.168.3.9     0.0.0.0         UG    100    0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth1
```


Did you bridge your virtualbox network cards to the correct physical network card from the base system?

Regards

---

### Post by SeijiSensei on 2012-01-18
> **Charlietje said:**
> from your configuration you have 2 default gateways. There can only be one "default"

Indeed.  If both routers can see the Internet, just pick one or the other.  If one subnet is busier than than other, pick the one that handles less traffic.

You'll need to make sure that the Linux box will forward packets (see /etc/sysctl.conf for details) and that any firewalling rules enables traffic between the two networks, or at a minimum, allows traffic from both networks to the Internet (in cases where you need to block traffic between the local networks for policy reasons).

---

### Post by luismpedro on 2012-01-18
> **SeijiSensei said:**
> Indeed.  If both routers can see the Internet, just pick one or the other.  If one subnet is busier than than other, pick the one that handles less traffic.

You'll need to make sure that the Linux box will forward packets (see /etc/sysctl.conf for details) and that any firewalling rules enables traffic between the two networks, or at a minimum, allows traffic from both networks to the Internet (in cases where you need to block traffic between the local networks for policy reasons).

Hi everyone, and thank you very much for trying to help. A few more details that I can give:
[LIST]
[*]removed the 192.168.2.1 as default gateway
[*]I'm using parallels workstation for the virtualization
[*]from another machine (192.168.2.11) that I've, I'm able to ping 192.168.2.12 (the eth1 from the base machine)
[*]Once I bring up the virtual machine 2 (192.168.2.15) from 192.168.2.11 I'm also able to ping 192.168.2.15. This means that, in some way, network is working. Still, I'm not able to access to ANYTHING from the second virtual machine :(
[/LIST]

Any other ideas?

Kind regards,

---

### Post by luismpedro on 2012-01-18
Hi again everyone,
   And while I was writing the previous reply I decided to restart my firewall system. Everything works after that! Sorry for the inconvenience and many thanks for all the help.

   Regards,
   LP

> **luismpedro said:**
> Hi everyone, and thank you very much for trying to help. A few more details that I can give:
[LIST]
[*]removed the 192.168.2.1 as default gateway
[*]I'm using parallels workstation for the virtualization
[*]from another machine (192.168.2.11) that I've, I'm able to ping 192.168.2.12 (the eth1 from the base machine)
[*]Once I bring up the virtual machine 2 (192.168.2.15) from 192.168.2.11 I'm also able to ping 192.168.2.15. This means that, in some way, network is working. Still, I'm not able to access to ANYTHING from the second virtual machine :(
[/LIST]

Any other ideas?

Kind regards,

---

