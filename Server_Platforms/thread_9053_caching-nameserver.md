---
title: "caching-nameserver"
date: 2004-12-23
forum: Server Platforms
---

### Post by chrisjones on 2004-12-23
I'm having trouble find the caching-nameserver package. I have enable universe and multiverse, yet synaptic does not find it. 

My main goal is to setup local DNS caching to speed up lookups instead of hitting my ISP everytime.

Any and all help would be appreciated.

---

### Post by p!=f on 2004-12-23
You might want to try dnsmasq
```

[~/src] > wajig show dnsmasq
Package: dnsmasq
Priority: optional
Section: universe/net
Installed-Size: 276
Maintainer: Simon Kelley <simon@thekelleys.org.uk>
Architecture: i386
Version: 2.19-1
Depends: netbase, libc6 (>= 2.3.2.ds1-4)
Suggests: resolvconf
Conflicts: pdnsd, resolvconf (<< 1.15)
Filename: pool/universe/d/dnsmasq/dnsmasq_2.19-1_i386.deb
Size: 102410
MD5sum: e262d3edb6697c3313f983da4c60ac54
Description: A small caching DNS proxy and DHCP server.
 Dnsmasq is lightweight, easy to configure DNS forwarder and DHCP
 server. It is designed to provide DNS and, optionally, DHCP, to a
 small network. It can serve the names of local machines which are
 not in the global DNS. The DHCP server integrates with the DNS
 server and allows machines with DHCP-allocated addresses
 to appear in the DNS with names configured either in each host or
 in a central configuration file. Dnsmasq supports static and dynamic
 DHCP leases and BOOTP for network booting of diskless machines.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

