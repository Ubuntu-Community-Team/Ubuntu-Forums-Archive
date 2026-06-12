---
title: "IPv6 gateway computer - routing help"
date: 2017-01-08
forum: Virtualisation
---

### Post by christina-korosec1 on 2017-01-08
I'm trying to use a linux VM as an IPv6 internet gateway for another VM.
I have a server installed for which I received the ipv6 prefix 2001:abcd:1234:5678::/64 *(Note I edited the prefixes for privacy reasons)*

device 1:
I put up interface eth0 (WAN) with address 2001:abcd:1234:5678:ffff::1/120
I put up interface eth1 (LAN) with IP fd12:3456:7890::1234

I used the following iptables rules:
```
-A FORWARD -o eth0 -i eth1 -s 2001:abcd:1234:5678:ffff::/120 -m conntrack --ctstate NEW -j ACCEPT
-A FORWARD -o eth1 -i eth0 -d 2001:abcd:1234:5678:ffff::/120 -m conntrack --ctstate NEW -j ACCEPT
-A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
```
Option is set correctly through sysctl: net.ipv6.conf.all.forwarding=1

The device can reach the IPv6 internet fine.

device 2:
I have eth0 with IP 2001:abcd:1234:5678:ffff::2/128 and gateway fd12:3456:7890::1234

I can reach both fd12:3456:7890::1234 and 2001:abcd:1234:5678:ffff::1 fine, but any outgoing connections to WAN hang as shown in conntrack on device 1:
```
tcp      6 118 SYN_SENT src=2001:abcd:1234:5678:ffff::2 dst=2a00:1450:400e:803::200e sport=43438 dport=80 [UNREPLIED] src=2a00:1450:400e:803::200e dst=2001:abcd:1234:5678:ffff::2 sport=80 dport=43438 mark=0 use=1
```
and the device 2's IP 2001:abcd:1234:5678:ffff::2 is not internet-resolvable, which is probably the cause of the hang.

What did I do wrong in my setup? How do I make the second device reach the internet through the first device?

See also [http://askubuntu.com/questions/869560/ipv6-gateway-computer-how-to-set-up-routing](http://askubuntu.com/questions/869560/ipv6-gateway-computer-how-to-set-up-routing)

---

### Post by wildmanne39 on 2017-01-08
*Thread moved to **Virtualisation**.*

---

### Post by geeksmith on 2017-01-12
Looks like you're trying to create a NAT-style setup, but didn't add any nat table rules. You can do IPv6 NAT, but it's generally discouraged. And using any subnet smaller than /64 is a huge no-no (larger prefix=smaller subnet).

Are you familiar enough with ip6tables to do the nat table rules? Should be similar to iptables.

---

