---
title: "Server become unreachable in Windows Domain"
date: 2011-07-13
forum: Server Platforms
---

### Post by tedknaz on 2011-07-13
Hi, I've got a Ubuntu 11.04 box running on our  primarily-Windows network. This is a bit of a noob question but I've  been unable to get a good answer just by lurking around in forums.

I've got two Windows Server 2003 DNS machines set up; they replicate any  DNS entries between themselves. The problem is that the ubuntu box  becomes unreachable by name maybe 2 hours after I register it with the  DNS. The setup is like this:
 

Ubuntu:
Static IP 192.168.1.X


 /etc/network/interfaces:
auto lo
iface lo inet loopback
 auto eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254
 post-up iptables restore < /etc/iptables.up.rules
 

/etc/resolv.conf:
domain domain.com
search domain.com
nameserver 192.168.1.2
nameserver 192.168.1.3


 /etc/hosts:
127.0.0.1 localhost
192.168.1.5 Hyperion.domain.com Hyperion
 

/etc/dhcp3/dhclient.conf (and /etc/dhcp/dhclient.conf):
send host-name "Hyperion";
request subnet-mask, broadcast-address, time-offset, routers, domain-name, domain-name-servers, domain-search, host-name, netbios-name-servers, netbios-scope, interface-mtu, rfc3442-classless-static-routes, ntp-servers;
 

The Windows DNS servers have Dynamic updates set to Secure only. They each have a Forward Lookup Zone Host (A) record:
Hyperion: 192.168.1.5


 No matter what I do, I can't seem to keep the ubuntu machine  reachable within the Windows domain. Does anyone have any idea what the  cause and solution to this problem may be? Thanks.

---

### Post by jmoorse on 2011-07-18
Does it stay reachable by IP?  

Eg: Can you ping 192.168.1.5 when you see it unreachable by pinging hyperion?

---

### Post by tedknaz on 2011-07-26
> **jmoorse said:**
> Does it stay reachable by IP?  

Eg: Can you ping 192.168.1.5 when you see it unreachable by pinging hyperion?

Yes, it always does. Apologies for the very delayed response.

---

