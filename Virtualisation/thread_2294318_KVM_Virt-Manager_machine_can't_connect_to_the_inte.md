---
title: "KVM Virt-Manager machine can't connect to the internet using br0"
date: 2015-09-10
forum: Virtualisation
---

### Post by pepsifx357 on 2015-09-10
I'm using Ubuntu 14.04.  I've successfully created a bridge, because the host has internet connection.  Everything seems to work fine, but when I use virt-manager and add br0 as the interface for the virtual machine, it doesn't work.

ip route
```
default via 1.1.1.2 dev br0 
1.1.1.0/24 dev br0  proto kernel  scope link  src 1.1.1.6 
10.0.0.0/15 dev virbr0  proto kernel  scope link  src 10.0.0.1 
169.254.0.0/16 dev br0  scope link  metric 1000 
```

/etc/network/interfaces
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

```

I had this working before.  I don't know why it's not working now.


Edit: DHCP it seems is the problem, because I can manually input the ip addresses for the virtual machines and they're connected.  What's the deal?

---

### Post by TheFu on 2015-09-26
Lots of things seem odd in the data above.
a) don't use network manager and bridges. Purge network manager to remove conflicts
b) how many many network interfaces does the machine have? All of them need to be in the interfaces file, if you want to use them.
c) Please post the complete interfaces file.
d) 1.1.1.0/24 ?  That IP really can't be used. Where did it come from?
e) Where/what is the DHCP server on this network?  If there are 2, which ever is fastest to answer "wins". If it is a router and a Linux PC, not such a big deal. 

There are lots of examples for setting up  a bridge with an IP out there. [http://blog.jdpfu.com/2013/11/03/setup-kvm-virtualization](http://blog.jdpfu.com/2013/11/03/setup-kvm-virtualization)  has the settings in an image (just click it).

Please post, using "code tags", the output from
[B]ifconfig
route
brctl
[/B]and
the complete contents of **/etc/network/interfaces** for more help.

---

