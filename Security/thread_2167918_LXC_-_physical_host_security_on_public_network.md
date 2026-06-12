---
title: "LXC - physical host security on public network"
date: 2013-08-15
forum: Security
---

### Post by jnorth on 2013-08-15
So, at my day job I use hardware firewalls, etc in front of virtual environments and am well versed in security from that front.  This question is more for home/small office type environments.

**TL;DR** - Assuming for simplicity that my IPTables configuration is 100% secure, how secure is LXC on an Ubuntu host box using a container-based iptables (shorewall) firewall, if the external interface has no IP address set?

**Full details** - I manage some small office environments that are usually using cable or DSL internet access, DHCP, and have little money in their budget for a decent hardware firewall platform, and usually do not want multiple devices, but want full service, (file server, database, mail, intranet web, OpenVPN, etc).  I used to use ProxMox and VMware for these guys and just run a security VM with iptables or pfSense firewall.

I have been playing with LXC and it is really something else.  What I am trying to find out how secure it is when set up the way I would like to do it.  Here is a fully working example running in my home lab right now.

Network config from LXC host below.  Diagram attached below that.

Just want to understand fully how this is working before I consider pushing out to a test client.

```
# loopback
auto lo
iface lo inet loopback


# bridge 0 (external wan)
auto br0
iface eth0 inet manual
iface br0 inet manual
 bridge_ports eth0
 bridge_fd 0
 bridge_maxwait 0
 mtu 1500


# bridge 1 (internal lan)
auto br1
iface eth1 inet manual
iface br1 inet static
 bridge_ports eth1
 bridge_fd 0
 bridge_maxwait 0
 address 192.168.101.201
 netmask 255.255.255.0
 network 192.168.101.0
 broadcast 192.168.101.255
 mtu 1500
 dns-nameservers 192.168.101.241 192.168.101.242
 dns-domain lxc.lab.point808.com
 gateway 192.168.101.251
```

[IMG]http://point808.com/Capture.JPG[/IMG]

---

