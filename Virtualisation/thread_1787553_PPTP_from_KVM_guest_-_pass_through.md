---
title: "PPTP from KVM guest - pass through"
date: 2011-06-21
forum: Virtualisation
---

### Post by kevpatts on 2011-06-21
Hey all,

I have a standard KVM guest using NAT and all normally works fine, it can browse the internet etc. no problem.

When I try to connect it to a PPTP VPN though it fails to connect. I've run Wireshark traces on the host machine and I can see the problem:
The PPP LCP configuration request gets to the PPTP server from the client, but it's response is blocked by my KVM host. Instead it returns an ICMP packet to say that the "destination unreachable (protocol unreachable)".

Any ideas how to fix this? I can't see many others with the same problem and I can't see any options for VPN pass through in the KVM network options.

Kevpatts

---

### Post by Jake.Debord on 2011-06-21
Try switching to a bridged connection, then see if that helps.

---

