---
title: "How to determine client DUID for stateful DHCPv6"
date: 2012-09-10
forum: Server Platforms
---

### Post by ocwo92 on 2012-09-10
I've setup a server for fixed DHCPv6 addresses for a number of clients using the Client DUID that appears in /var/lib/dhcp/dhclient-*.lease when the client first connects. I'm using the ISC DHCP server.

However, at this point the client has already received an undesired IPv6 address.

How do I determine the Client DUID before the client performs its first DHCPv6 request?

---

### Post by anonymouschief on 2012-10-15
I was under the impression that IPv6 uses MAC addresses as an identifier to assign static IPs.

I am running DHCP to assign statis IPv4 addresses as well as dynamic ones to my LAN. I use the MAC address to identify the machines, which I then assign a statis IP. Here is at example assignment in /etc/dhcp/dhcpd.conf

```

host SuperFast {
  hardware ethernet 8b:f5:3d:5b:9e:22;
  fixed-address 192.168.0.100;
}

```

The DHCP Server identifies that client by its MAC address and then assigns the .100 IP address to that client. Let me know if you would like to see the whole conf file.

---

### Post by ocwo92 on 2012-10-16
> **anonymouschief said:**
> I was under the impression that IPv6 uses MAC addresses as an identifier to assign static IPs.
Yes, IPv6 includes the MAC addresses as part of the DUID, but the DUID contains more than that. I'm interested in knowing an actual algorithm or similar for calculating the DUID.

> I am running DHCP to assign statis IPv4 addresses as well as dynamic ones to my LAN. I use the MAC address to identify the machines, which I then assign a statis IP.
I do this for IPv4 addresses, too, but from what I gather, this feature is intentionally not supported with IPv6. I'm not entirely sure why, although MAC address spoofing seems like an obvious reason.

---

### Post by anonymouschief on 2012-10-24
Now I want to to know more about this. So far, all I can tell is that the DUID, once generated, gets saved into /etc/dhcpcd.duid.

I will keep searching and let you know if I find anything else.

---

### Post by ocwo92 on 2012-10-24
> **anonymouschief said:**
> Now I want to to know more about this.
A while back I stumbled across this script: [http://www.tc.mtu.edu/ipv6/wide_mkduid.pl](http://www.tc.mtu.edu/ipv6/wide_mkduid.pl) when I searched for a DUID algorithm, but it doesn't generate the DUIDs that my own system assigns to its clients.

I think I read somewhere that the DUID generated in part by (some of) the MAC address of the network card and in part by the current time, and that it is not required to be generated according to a particular algorithm; if anyone can enlighten me on this, please let me know.

---

### Post by H3g3m0n on 2013-09-19
At the risk of thread necromancy (this came up in Google for me).
[http://ipv6friday.org/blog/2011/12/dhcpv6/](http://ipv6friday.org/blog/2011/12/dhcpv6/)

---

