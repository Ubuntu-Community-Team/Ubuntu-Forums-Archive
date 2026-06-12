---
title: "brctl addif br0 eth0 kills the networking"
date: 2016-01-16
forum: Virtualisation
---

### Post by gnumster on 2016-01-16
Hi there,
I have decided to start asking around after two days of struggling with this matter, and re-installing my whole ubuntu server twice already. Can't seem to get to resolution myself so need help!

The intention is to use libvirt for hosting a number of VMs on a single ubuntu server host. All VMs are intended to share the same eth0 for accessing the network outside the host machine. For that purpose I am setting up br0 to link to eth0... and the moment I do that - the host becomes unreachable from the network.

This is what my /etc/network/interfaces looks like in the failure state:

-----------------------------------------------------------------------
source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface - USED FOR VMs
auto eth0
iface eth0 inet static
        address 192.168.1.5
        network 192.168.1.0
        netmask 255.255.255.0
        gateway 192.168.1.1
        broadcast 192.168.1.255
        dns-nameservers 203.96.123.1 203.96.123.2 8.8.8.8


# The bridge for virtual machines
auto br0
iface br0 inet static
        bridge_ports eth0
        address 10.0.0.1
        network 10.0.0.0
        netmask 255.255.255.0
        broadcast 10.0.0.255
        gateway 192.168.1.1
        dns-nameservers 203.96.123.1 203.96.123.2 8.8.8.8
    bridge_stp off
    bridge_fd 0
    bridge_maxwait 0
-----------------------------------------------------------------------

If I comment the line "bridge_ports eth0" and reboot - all goes well, except there is not "br0" appears in ifconfig report, and none of the VMs would be able to start.

I have already tried to do everything I could think of from changing address allocations from static to dhcp, from same network to different. Tried to enable eth1 and use it as additional channel for external traffic. Tried resetting firewall, tried doing "route add" in a number of way - nothing helps.

Strage enough - it used to work before, and it was nothing fancy in terms of getting to working state. Just added "br0" into interfaces, installed libvirt, used "virsh" to deal with VMs - all was hunky dory. Then something happened and now even complete re-install of the entire Ubuntu to latest version (15.10 GNU/Linux 4.2.0-23-generic x86_64) won't make a difference.

Any ideas anyone?

---

### Post by Doug S on 2016-01-16
Typically a bridge is used so that the quest VM's can be put on the same LAN sub-net as the host. You are trying to do 2 sub-nets. The suggestion is to have everything on the one 192.168.1.0 sub-net:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface and bridge
auto br0
iface br0 inet static
bridge_ports eth0
address 192.168.1.5
network 192.168.1.0
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 203.96.123.1 203.96.123.2 8.8.8.8
bridge_stp off
bridge_fd 0
bridge_maxwait 0
```

---

### Post by gnumster on 2016-01-16
Thank you Doug,
much appreciate the response!

I have tried that too. In fact that is what I have started from when it went wrong. Moveingthe bridge onto a different subnet was an attempt to fix it.

---

### Post by Doug S on 2016-01-16
> **gnumster said:**
> I have tried that too. In fact that is what I have started from when it went wrong. Moveingthe bridge onto a different subnet was an attempt to fix it.And the symptoms are exactly the same? Could you describe your network more. Also this is my interfaces file, as taken from [here]("https://help.ubuntu.com/lts/serverguide/network-configuration.html#bridging").```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface and bridge
auto br0
iface br0 inet dhcp
#iface br0 inet static
#  address 192.168.111.112
#  network 192.168.111.0
#  netmask 255.255.255.0
#  gateway 192.168.111.1
#  broadcast 192.168.111.255
#  dns-search smythies.com
#  dns-nameservers 192.168.111.1
  bridge_ports eth0
  bridge_fd 9
  bridge_hello 2
  bridge_maxage 12
  bridge_stp off

```Try those bridge settings.

---

### Post by MAFoElffen on 2016-01-16
Confirmed & plus one with DougS...

Here is one of mine:
```

# snoopy is eth2 & eth 3

# The primary network interface
auto eth2
iface eth2 inet static
    address 192.168.2.15
    netmask 255.255.255.0
    network 192.168.2.0
    broadcast 192.168.2.255
    gateway 192.168.2.1
    dns-search ferreiraent.com

# The secondary interface
auto br0
iface br0 inet static
    address 192.168.2.17
    netmask 255.255.255.0
    network 192.168.2.0
    gateway 192.168.2.1
    broadcast 192.168.2.255
    metric 1
    bridge_ports eth3
    bridge_fd 9
    bridge_hello 2
    bridge_maxage 12
    bridge_stp off

```
That config is actually 2 NICs on the same NID, but same concepts... The problem I found to that you just need the the "iface br0" definition and bind it to the NIC/port you are using... The doc's don't say, this = found out the hard way, but... Just one config definition per NIC. If you have two (one for the port and one for the bridge), then they conflict as two definitions for the same port. The br0 define covers it all. Just like in both mine and Doug's, the key line is bind line
```

bridge_ports <port>

``` 
I had previously tried what the the Ubuntu [NetworkConnectionBridge]("https://help.ubuntu.com/community/NetworkConnectionBridge") Wiki page has an example of:
```

auto lo
iface lo inet loopback

iface eth0 inet manual

iface eth1 inet manual

auto br0
iface br0 inet dhcp
  bridge_ports eth0 eth1

```
And to be honest with you, that did not work out so well for me... but I latter found this example from the Ubuntu [KVM/Networking]("https://help.ubuntu.com/community/KVM/Networking") Wiki page:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 192.168.0.10
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

```
And that did work for me. That is where I got the info for the start of my settings, then tuned from there. (re: [man interfaces]("http://manpages.ubuntu.com/manpages/trusty/man5/interfaces.5.html"))

So if you took yours and tried something like this (edited to your settings):
```

# The loopback network interface
auto lo
iface lo inet loopback

# Eth0 is also the bridge for virtual machines
auto br0
iface br0 inet static
    address 192.168.1.5
    network 192.168.1.0
    netmask 255.255.255.0
    gateway 192.168.1.1
    broadcast 192.168.1.255
    dns-nameservers 203.96.123.1 203.96.123.2 8.8.8.8
    bridge_ports eth0
    bridge_fd 0
    bridge_stp off
    bridge_maxwait 0

```
On a different perspective, if you wanted to, you can bind multiple virtual networks with different NID's through one NIC. (Which varies from what Doug S said...) But not by using a bridge. A bridge is to "bridge" or span from point A to point B using the same NID, so in this case, to the same NID as the host. Other methods to do binds to other NID's are NAT, vlan, & macvlan. you can bind NAT to a port that is bound to other things. With vlan, you bind multiple vierual newtorks to the same device. With macvlan, you create multiple viertual mac addresses to bind a virtual network to each, allowing multiple virtual networks through one NIC. Or a custom virtual network. I have a virtual router running as a VM, then a VM Server w/ multiple virtual NIC's doing routing and bridging. Let your imagination roam.

And ... as a sidenote, I noticed you have 3 dns-search Ip's listed. The old doc's said that we could have 4 dns-search IP addresses, separated by a space, in the interfaces file. That changed over 4 years during the dev cycle for 12.04 when resolv.conf was changed from a hard file to being dynamically built during boot. T hen noticed that that adding more than 2 dns-search IP's to the interfaces file, anything after that what fall out. After noticing that, I had to do some research on how to do that. I have a local primary and secondary DNS, so my local machines need both those, then an upstream DNS IP as a backup, so I needed 3 listed. If you create a /etc/resolvconf/resolv.conf.d/tail file, then add those ip addresses to that file, then those get appended to the end of the dynamically built resolve.conf.

---

