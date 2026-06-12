---
title: "IPSec Networking to LAN"
date: 2009-07-01
forum: Security
---

### Post by TorchlightJay on 2009-07-01
Hello,
    This seems to be the proper place to put this question. I am currently working on an IPSec VPN on and Ubuntu 9.04 system. This device not only serves as an IPSec device but it is also our NAT and DHCP. We are trying to create a tunnel between an office about 100 miles away and my office here. Though we have created the tunnel, they are giving us an IP from a completely different network. Example, they are giving us 172.x.x.x and we are 192.168.x.x. I need the tunnel to simply connect to one box on my network. How do I go about doing this when they are giving me an IP that my network doesn't suppotr?

---

### Post by koenn on 2009-07-02
> **TorchlightJay said:**
> Hello,
    This seems to be the proper place to put this question. I am currently working on an IPSec VPN on and Ubuntu 9.04 system. This device not only serves as an IPSec device but it is also our NAT and DHCP. We are trying to create a tunnel between an office about 100 miles away and my office here. Though we have created the tunnel, they are giving us an IP from a completely different network. Example, they are giving us 172.x.x.x and we are 192.168.x.x. I need the tunnel to simply connect to one box on my network. How do I go about doing this when they are giving me an IP that my network doesn't suppotr?

maybe you need to set up routes on each of the networks' default gateway, routes pointing to the other network

You may also want to consider replacing IPsec with Openvpn. IPsec is notoriously difficult, especially when you need to traverse NAT. Openvpn is a valuable alternative that's quite easy to get up and running.

[http://openvpn.net/](http://openvpn.net/)

---

### Post by SmarterThanMyPhone on 2009-07-02
set up a dhcp pool on the device (cisco?) and statically set IP's from that pool on your pc.

---

