---
title: "Binding KVM VMs to an OpenVPN network?"
date: 2009-06-20
forum: Server Platforms
---

### Post by mlaccetti on 2009-06-20
The question:
Is it possible to get my 192.168.250.x KVM VMs to show be shared with my 10.0.1.0 VPN machines?  If I migrated to 10.0.2.0 and setup the VPN to route accordingly, would that be the easiest solution?

The setup:
I have an Ubuntu server with an external IP (76.73.x.x, br0) that acts as my OpenVPN hub (10.0.0.1, tun0).  Running on it are four KVM VMs, all 76.73.x.x external IPs and 192.168.250.x internal IPs, attached to vibr0.  I have attached a PNG with the setup.

---

### Post by samosamo on 2009-06-22
Why wouldn't it be possible?  What are your challenges?  I see you have 2 options: one would be add a route to your gateway, the other would be set up an openvpn server in bridge mode.  Both would work just fine.

---

### Post by mlaccetti on 2009-06-28
I should have really asked for directions on how to do so.  :)  Basically, I don't want to fiddle around with tun0 or br0, since it is a remote server and any problems involve external support.

---

