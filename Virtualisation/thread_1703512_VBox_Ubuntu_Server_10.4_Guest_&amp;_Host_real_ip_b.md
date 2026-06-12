---
title: "VBox Ubuntu Server 10.4 Guest &amp; Host real ip bridge"
date: 2011-03-09
forum: Virtualisation
---

### Post by iLLiCiTgr on 2011-03-09
Hello.
I'm renting a server abroad i want to install a VBox VMachine as part of a project we are developing.

I've successfully created the virtual machine via vboxmanage.
But now before continuing with the installation, i'd like to give the vmachine access to the internet.
I have 2 IPs available on the server. 1 on the real adapter eth0 (188.40.xxx.119) and 1 on the virtual adapter eth0:1 (188.40.xxx.120)

Lets say i want to assign the .120 to the server via bridge.

I've read [http://www.virtualbox.org/wiki/Advanced_Networking_Linux](http://www.virtualbox.org/wiki/Advanced_Networking_Linux)

```
#!/bin/sh
# set PATH for the case we are called via sudo or su root

PATH=/sbin:/usr/bin:/bin:/usr/bin

# create a tap
tunctl -t tap1 -u <user>
ip link set up dev tap1
f
# create the bridge
brctl addbr br0
brctl addif br0 tap1

# set the IP address and routing
ip link set up dev br0
ip addr add 10.1.1.1/24 dev br0
ip route add 10.1.1.0/24 dev br0

```

But since my primary ip address and my secondary are on the same subnet, i  think by just replacing 10.1.1.1 and 10.1.1.0 with 188.40.xxx.120 and 188.40.xxx.0 accordingly will just route all the server traffic through the br0 interface?

I suck @ networking.. Any help would be greatly appreciated.

---

### Post by iLLiCiTgr on 2011-03-14
Anyone?  Any help would be greatly appreciated

---

