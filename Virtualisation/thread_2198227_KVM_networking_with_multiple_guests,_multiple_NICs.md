---
title: "KVM networking with multiple guests, multiple NICs one one network"
date: 2014-01-07
forum: Virtualisation
---

### Post by BarryDocks on 2014-01-07
I am having a bit of trouble configuring a stable network with multiple linux guests each on indervidual NICs all on the same network, in fact I am not sure if what I am doing is the most effective method to achieve what I want.

So here is the goal:

Host OS is ubuntu 12.04 LTS 64bit headless runing on HP Prolient ML115 AMD Quad core with 8GB (MAX) RAM and 4gigabit NICS
eth0 - WAN
eth1, eth2, eth3 - LAN

Guest 1:
Zentyal 2.2 (ubuntu 10.04) 64bit acting as a gateway, dhcp server, DNS server, etc for the local network with 2 virtio NICs
eth0 bridged to the WAN 
eth1 bridged to the LAN

Guest 2:
OpenMediaVault (debian 6?) 64bit acting as a file server to the LAN with 1 virtio NIC
eth0 bridged to the LAN

Guest 3: 
Ubuntu 6.06 64 bit with MYSQL 4.1 (needed for legacy purposes) on the LAN with e1000 NIC (virtio is not supported in this version of ubuntu)
eth0 bridged to the LAN

I initally wanted a bonded interface on the host but rapidly gave up on this as it would also invole creating virtual adaptors of the bond, ie one for each guest?
So my interfaces file on the host looks liek this:
```

auto lo
iface lo inet loopback

##########################
##WAN interface & bridge##
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
  bridge_ports eth0
  bridge_stp off
  bridge_fd 0
  bridge_maxwait 0
##########################

##########################
##LAN interfaces & bridge##
auto eth1
iface eth1 inet manual

auto eth2
iface eth2 inet manual

auto eth3
iface eth3 inet manual

auto br1
iface br1 inet static
  address 10.0.0.1
  netmask 255.255.255.0
  bridge_ports eth1 eth2 eth3
  bridge_stp off
  bridge_fd 0
  bridge_maxwait 0
##########################


```

This would work initally but a simple reboot of the host and then there would be no connections to the LAN for the host or any guests and the LEDs in the host NICs just bink rapidly.  The NICs are a mix of both broadcom and Intel.

I am not entiely sure what is going wrong or if there is a better way of doing it, possibly with an internal host network that breaks out to the LAN?

In the meantime I have gone back to Virtualbox but the network performanace is about a 1/3 of KMV :-(

---

### Post by TheFu on 2014-01-07
Yep, virtualbox has more overhead than straight Linux bridges. That is to be expected.

I haven't a clue about how to accomplish what you want, but the "manual" startups for every interface seemed out of place to me. Are you sure that setting is what you want?

There is only 1 bridge there. Don't you need at least 2?

---

### Post by mageta2 on 2014-01-18
Just a thought, if you want to host a bunch of machines on one system, you should read up on type 1 hypervisors. Rather than having a host OS with virtualization software, the OS IS the virtualization software, thus giving you more direct access to the hardware. Eli the computer guy has a great video on this.

---

### Post by BarryDocks on 2014-01-18
> **mageta2 said:**
> Just a thought, if you want to host a bunch of machines on one system, you should read up on type 1 hypervisors. Rather than having a host OS with virtualization software, the OS IS the virtualization software, thus giving you more direct access to the hardware. Eli the computer guy has a great video on this.
I think you will find that installing KVM in linux turns the kernel into a type 1 hypervisor
[http://en.wikipedia.org/wiki/Hypervisor]("http://en.wikipedia.org/wiki/Hypervisor")

The other reason for using ubuntu as a host is that it's free and I want to be able to connect to a ups for a gracefull shutdown in the event of a power failure, from what I understand this is difficult to do in ESXi

I think I'll re-post this in the networking section

---

