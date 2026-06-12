---
title: "How to create br0 on KVM?"
date: 2010-09-21
forum: Server Platforms
---

### Post by pungki on 2010-09-21
Hi all,

I have Ubuntu 9.10 Karmic install on the server machine and I'm new about virtualization.

I want to install Virtual Server above it via KVM to be used as development server. I found Jeos documentation ([https://help.ubuntu.com/community/JeOSVMBuilder](https://help.ubuntu.com/community/JeOSVMBuilder)) and [http://embr.cygni.se/forme/?p=72](http://embr.cygni.se/forme/?p=72)

The goal is I want let the developers, programmers access the development server from internet, and do they experiment on it.

But I don't understand this section :

auto br0
iface br0 inet static
        address 192.168.10.100
        network 192.168.10.0
        netmask 255.255.255.0
        broadcast 192.168.10.255
        gateway 192.168.10.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

Here's my /etc/network/interfaces :

auto lo
iface lo inet loopback

auto eth0

iface eth0 inet static

        address 202.51.a.b
        netmask 255.255.255.x

        broadcast 202.51.x.2

        gateway 202.51.x.1

I add br0 section above to my interfaces, and when I restart it, it failed.

Why do we need bridge if I can use Public IP?

---

### Post by senor_smile on 2011-01-10
> **pungki said:**
> Hi all,

I have Ubuntu 9.10 Karmic install on the server machine and I'm new about virtualization.

I want to install Virtual Server above it via KVM to be used as development server. I found Jeos documentation ([https://help.ubuntu.com/community/JeOSVMBuilder](https://help.ubuntu.com/community/JeOSVMBuilder)) and [http://embr.cygni.se/forme/?p=72](http://embr.cygni.se/forme/?p=72)

The goal is I want let the developers, programmers access the development server from internet, and do they experiment on it.

But I don't understand this section :

auto br0
iface br0 inet static
        address 192.168.10.100
        network 192.168.10.0
        netmask 255.255.255.0
        broadcast 192.168.10.255
        gateway 192.168.10.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

Here's my /etc/network/interfaces :

auto lo
iface lo inet loopback

auto eth0

iface eth0 inet static

        address 202.51.a.b
        netmask 255.255.255.x

        broadcast 202.51.x.2

        gateway 202.51.x.1

I add br0 section above to my interfaces, and when I restart it, it failed.

Why do we need bridge if I can use Public IP?

You need a bridge to "bridge" the physical eth0 of the host machine with the virtual nic's on the vm's.  Without this the internal virtual nic's of the vm's are on an internal isolated network; i.e. no traffic can pass directly from the internet to the vm's.  The nat that is set up by default acts as a firewall, only letting traffic in that was initiated by the vm's.

---

