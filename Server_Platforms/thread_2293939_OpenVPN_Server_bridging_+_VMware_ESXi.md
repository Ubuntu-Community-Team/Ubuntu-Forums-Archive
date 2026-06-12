---
title: "OpenVPN Server bridging + VMware ESXi"
date: 2015-09-08
forum: Server Platforms
---

### Post by Philip2222 on 2015-09-08
Hi,
I'm having problems with bridging traffic between tap0 (OpenVPN interface) and eth0 in my br0 bridge. My Ubuntu server is running as a VM on VMware ESXi (vSphere 5.5). My VPN client connects to the server successfully but can't reach anything on the server network except br0. I'm using brctl to create br0 which bridges eth0 and tap0. I have also enabled promiscuous mode on eth0, tap0 and in the distributed port group in VMware.

This is my network interface configuration.

/etc/network/interfaces
```

auto eth0
iface eth0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  down ifconfig $IFACE down


auto br0
iface br0 inet dhcp
  bridge_ports eth0

```

```

# brctl show br0
bridge name     bridge id               STP enabled     interfaces
br0             8000.44444445bc53       no              eth0
                                                        tap0

```


This is my up.sh file triggered by /etc/openvpn/server.conf: up.sh br0 eth0 1500
```

#!/bin/sh


BR=$1
DEV=$2
MTU=$3
/sbin/ifconfig $DEV mtu $MTU promisc up
/sbin/brctl addif $BR $DEV

```
This is my down.sh file triggered by /etc/openvpn/server.conf: down.sh br0 eth0
```

#!/bin/sh


BR=$1
DEV=$2


/sbin/brctl delif $BR $DEV
/sbin/ifconfig $DEV down


```

```

ifconfig
br0       Link encap:Ethernet  HWaddr 44:44:44:45:bc:53
          inet addr:10.13.37.102  Bcast:10.13.37.255  Mask:255.255.255.0
          inet6 addr: fe80::4644:44ff:fe45:bc53/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7957 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6839 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:896520 (896.5 KB)  TX bytes:1108358 (1.1 MB)


eth0      Link encap:Ethernet  HWaddr 44:44:44:45:bc:53
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:6590 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8618 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:870520 (870.5 KB)  TX bytes:1291596 (1.2 MB)


tap0      Link encap:Ethernet  HWaddr fa:17:3e:62:80:0a
          inet6 addr: fe80::f817:3eff:fe62:800a/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:1890 errors:0 dropped:13 overruns:0 frame:0
          TX packets:2044 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:195046 (195.0 KB)  TX bytes:223883 (223.8 KB)

```

I'm running the OpenVPN server in client-to-client mode.

When i try pinging (ICMP) another server on the server side 10.13.37.101 from the VPN client I don't get any reply and the ARP requests is not sent back to the client machine.
```

sudo tcpdump -v "icmp or arp" -i eth0 -vvv
tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
19:06:38.894179 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 10.13.37.101 tell 10.13.37.251, length 28
19:06:38.894296 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 10.13.37.101 tell 10.13.37.251, length 46
19:06:38.894310 ARP, Ethernet (len 6), IPv4 (len 4), Reply 10.13.37.101 is-at 44:44:44:d2:9d:17 (oui Unknown), length 46


sudo tcpdump -v "icmp or arp" -i br0 -vvv
sudo: unable to resolve host 30a648b045ae4e3db55e8c7797f899d8-vpn
tcpdump: listening on br0, link-type EN10MB (Ethernet), capture size 65535 bytes
19:37:45.341274 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 10.13.37.101 tell 10.13.37.251, length 28
19:37:45.341430 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 10.13.37.101 tell 10.13.37.251, length 46
19:37:45.341459 ARP, Ethernet (len 6), IPv4 (len 4), Reply 10.13.37.101 is-at 44:44:44:d2:9d:17 (oui Unknown), length 46

sudo tcpdump -v "icmp or arp" -i tap0 -vvv
sudo: unable to resolve host 30a648b045ae4e3db55e8c7797f899d8-vpn
tcpdump: WARNING: tap0: no IPv4 address assigned
tcpdump: listening on tap0, link-type EN10MB (Ethernet), capture size 65535 bytes
19:39:12.658904 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 10.13.37.101 tell 10.13.37.251, length 28
19:39:12.659186 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 10.13.37.101 tell 10.13.37.251, length 46
19:39:13.383365 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 10.13.37.101 tell 10.13.37.251, length 28



```

I have seen this [http://serverfault.com/questions/337952/arp-reply-vanishes-from-br0-to-tap0-using-openvpn-in-bridging-mode](http://serverfault.com/questions/337952/arp-reply-vanishes-from-br0-to-tap0-using-openvpn-in-bridging-mode) but Net.ReversePathFwdCheckPromiscNet.ReversePathFwdCheckPromisc (set to 1) is already enabled on my ESXi hosts. 
-------
Philip

---

### Post by darkod on 2015-09-08
Can we go a step back and discuss your setup and why/if you need it? This looks to me too complex, and not needed. Vmware is very good with its vSwitches and you basically rarely need to use br0. Only the standard eth0.

Also, isn't 10.13.37.x part of the private 10.0.0.0/8 range. Do you have a public IP at all? Or more of them?

---

### Post by Philip2222 on 2015-09-08
My VMware vSphere is the infrastructure for my OpenStack deployment (HP CloudSystem) and I want to deploy OpenVPN as Cloudpipe in OpenStack. Therefore I want to use a bridge on the VM instance instead of having to add configuration to the vSphere environment. This has been straightforward on KVM hypervisors but not on VMware ESXi. 

Yes the IP subnet is private but I'm using NAT to make the OpenVPN server public accessible. There are no problems establishing the connection from the client to the server. The issue is the traffic flow on the VM's bridge.

---

### Post by darkod on 2015-09-09
If these instructions are up to date, they seem to be creating br0 with the bridge-start script, not like you did in /etc/network/interfaces.
[https://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html](https://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html)

Or am I reading it wrong? Do you think creating br0 like they did might make a difference?

PS. Also, when creating a bridge in /etc/network/interfaces, shouldn't the eth0 stanza be just:
```
auto eth0
iface eth0 inet manual
```

I have that on my KVM host. I don't understand the purpose of the additional two lines you have for eth0. You want to work with br0 anyway, eth0 is not important, right?

---

### Post by Philip2222 on 2015-09-09
Hmm, I don't think that should do any difference since my bridge is showing up as expected when running brctl showmacs br0.

In my /etc/networking/interfaces file I'm reseting the IP of eth0 and then taking the interface down. I have tried to follow this instructions [http://docs.openstack.org/developer/nova/devref/cloudpipe.html](http://docs.openstack.org/developer/nova/devref/cloudpipe.html)

I want to work with br0 which bridges eth0 and tap0. br0 is the only interface with IP.

Any clue?

---

### Post by darkod on 2015-09-09
Well, I'm no expert on bridging but in my KVM setup I am not bringing eth0 down. The instructions I found when setting it up never mentioned something like that. And it works perfect. You might try commenting out the up and down lines for eth0. However this is just an idea, I don't see the setup as a mistake... But since it doesn't work as you want to, you might try other ideas.

Also I would do the up.sh and down.sh as per that openvpn webpage instructions, not the cloudpipe. All they do on the page you linked is setting up and bringing the interfaces up. You have that in the openvpn instructions too.

See how that goes... It's the only idea I've got right now.

---

### Post by Philip2222 on 2015-09-09
Okay but my eth0 is then brought online in up.sh. I have copied the configuration to a VirtualBox VM (this is the image for the VMware VM) on my local machine and I can successfully connect to it and transfer traffic over the bridge. 
The only difference between the VM on my local machine and the one running in VMware is the hypervisor and that the VMware image has cloud-init for initialization in my OpenStack environment.

I have suspicions that either the ESXi hypervisor environment or cloud-init is preventing my bridge from functioning as intended.

----------
Philip

---

### Post by Philip2222 on 2015-09-09
> **Philip2222 said:**
> Okay but my eth0 is then brought online in up.sh. I have copied the configuration to a VirtualBox VM (this is the image for the VMware VM) on my local machine and I can successfully connect to it and transfer traffic over the bridge. 
The only difference between the VM on my local machine and the one running in VMware is the hypervisor and that the VMware image has cloud-init for initialization in my OpenStack environment.

I have suspicions that either the ESXi hypervisor environment or cloud-init is preventing my bridge from functioning as intended.

----------
Philip

I have also tried to deploy an OpenVPN Access Server appliance in VMware. In L3 mode I can successfully reach the servers trough the VPN tunnel but as soon as I switch over to L2 I get the same result as with my own VM image in VMware.

Is there anyone who has had problems with the layer 2 bridging OpenVPN on VMware ESXi? I have seen this also [http://www.jeremycole.com/blog/2010/03/11/openvpn-bridge-under-vmware-esxi/](http://www.jeremycole.com/blog/2010/03/11/openvpn-bridge-under-vmware-esxi/) but since I'm using dvSwitch I have enabled promiscuous mode on the distributed port group. I'm thinking it is maybe worth trying to connect the OpenVPN appliance using a standard vSwitch instead.

EDIT: I want to use L2 mode since I don't want my customers networks (any RFC1918) to collide with the VPN pool.

---

### Post by Philip2222 on 2015-09-11
My misstake! I hade only enabled Net.ReversePathFwdCheckPromiscNet.ReversePathFwd and not Net.ReversePathFwdCheckPromiscNet.ReversePathFwdCheckPromisc on my ESXis hosts. This must be enabled due to that the dvSwitch with distributed port groups in promiscious mode with mutliple uplink uplinks (team) causes multicast and broadcast traffic to loop back to the host which in turn causes ARP to fail. 

SOLVED

---

