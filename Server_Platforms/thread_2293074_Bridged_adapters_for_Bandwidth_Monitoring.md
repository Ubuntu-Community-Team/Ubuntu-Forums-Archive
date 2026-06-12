---
title: "Bridged adapters for Bandwidth Monitoring"
date: 2015-09-02
forum: Server Platforms
---

### Post by dublea on 2015-09-02
Good morning Ubuntu Forums!

So, I'm banging my head against a wall here trying to figure out how to do this.  First off, let me say that I'm doing testing in Virtualbox before I attempt on a physical device and network.  In the past I've used ntop for bandwidth monitoring but in these cases the linux box was acting as DHCP, DNS, etc.  This made it easy as it was already in place.  But, now I'm trying to setup and configure a server like the topology here:

[IMG]http://i.imgur.com/XsvYFp7.png[/IMG]

It needs to be able to be attached to the network in a way that all traffic has to pass between it and the outside world.  I'm trying to set this up for not only myself, but future reference if the case is needed.  In my case I'm in a Comcast test market where they've started charging for going over my allotted 300GB.  So, I want to know what service, device, etc, on my network is using the most amount of data.  I also want to compare their crappy meter to see how accurate it really is.  I don't believe it's accurate at all...

So, I've setup multiple devices in for my test in virtualbox.  Listed below are the devices and how their NIC's have been configured in vbox:

[LIST=1]
[*]Ubuntu Server with ntopng installed
[LIST]
[*]eth0 - Attempted both NAT and Bridged vbox NICs
[*]eth1 - Internal Network
[/LIST]
[*]TestBox01 - Ubuntu Desktop
[LIST]
[*]eth0 - Internal Network
[/LIST]
[*]TestBox02 - Windows 7
[LIST]
[*]eth0 - Internal Network
[/LIST]
[/LIST]

Utilizing [this documentation]("https://help.ubuntu.com/community/NetworkConnectionBridge") I was able to bridge eth0 & eth1 to br0.  The Ubuntu Server can still ping out and is assigned an IP via DHCP.  

When I run 'brctl show' I receive the following:

```
bridge name		bridge id			STP enabled		interfaces
br0			8000.0800273cd058		no			eth0
										eth1
```

When I run 'ip addr show' I receive the following:

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default
	link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
	inet 127.0.0.1/8 scope host lo
		valid_lft forever preferred_lft forever
	inet6 ::1/128 scope host
		valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UP group default qlen 1000
	link/ether 08:00:27:3c:d0:58 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UP group default qlen 1000
	link/ether 08:00:27:cc:6f:9a brd ff:ff:ff:ff:ff:ff
	inet6 fw80::a00:27ff:fecc:6f9a/64 scope link
		valid_lft forever preferred_lft forever
4: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default
	link/ether 08:00:27:3c:d0:58 brd ff:ff:ff:ff:ff:ff
	inet 10.0.2.15/24 brd 10.0.2.255 scope global br0
		valid_lft forever preferred_lft forever
	inet6 fe80::a00:27ff:fe3c:d058/64 scope link
		valid_lft forever preferred_lft forever
```

My /etc/networking/interfaces file is currently configured as:

```
auto lo br0
iface lo inet loopback

iface eth0 inet manual

iface eth1 inet manual

iface br0 inet dhcp
	bridge_ports eth0 eth1
	bridge_fd 0
	bridge_maxwait 0
	bridge_stp off
```

The issue, when either of the test boxes connect, they obtain IP, DNS, gateway, etc, from the NAT or Bridged DHCP servers.  When I had the eth0 bridged in vbox, I verified with my firewall that handles DHCP that it received the request and provided an IP.  But, from either of the test boxes I cannot ping the DHCP server, gateway, or anything.  I don't know if this is even possible the way I'm attempting but based on the linked NetworkConnectionBridge documentation, it's precisely what I'm looking for.  Any advice would be appreciated!

EDIT:  Here is a topology of the virtual setup I'm trying to create:

[IMG]http://i.imgur.com/ETRG1qL.png[/IMG]

I also found [this troubleshooting]("http://www.microhowto.info/troubleshooting/troubleshooting_ethernet_bridging_on_linux.html") guide... but it all looks configured and setup correctly.  I'm still pushing to try to figure this out on my own.  At least if I can get it working I'll have documented the process.  Again, any advice would be appreciated!

EDIT 2:  OK, silly me.  I created another VM with Untangle installed.  I created it with two nics and configured it as a firewall/router.  I then adjusted the nic adapters of the other VMs to point to another Internal Network.  And now it's all working fine.  Now time to build the box and deploy.

---

