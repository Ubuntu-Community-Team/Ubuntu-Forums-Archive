---
title: "Help setting up iptables for Symmetric NAT"
date: 2011-04-14
forum: Server Platforms
---

### Post by walidch on 2011-04-14
Hello everyone,

I am having difficulties setting up Symmetric NAT through iptables and I hope you can help me with this issue.

_First things first:_
[B]"A symmetric NAT is one where all requests from the same internal  IP address and port, to a specific destination IP      address and  port, are mapped to the same external IP address and port.  If the same  host sends a packet with the same source      address and port, but to a  different destination, a different mapping is used.  Furthermore, only  the external host that       receives a packet can send a UDP packet  back to the internal host."

[/B][U]Need:
[/U]I am working on a SIP application and SIP apps face a problem with NATed networks. 
STUN is a solution to such a problem and my SIP application has an embedded STUN client functionality.

_Scenario and Technical Details:_


192.168.0.200
+-----------------+
| ClientA - My IP |
+-----------------+
|
|GW:
| eth0         eth1 (example public IP address)
| 192.168.0.1 | 123.123.123.123
+-------------|-------------+
|   NAT1   |
+-------------|-------------+
|
|
|
stun.1und1.de |
+---------------------------+
|    STUN Server        |
+---------------------------+

I am using WinSTUN, which requires a STUN Server address (such as the one I specified above) to return my type of NAT.

What I need to achieve is _Symmetric NAT through iptables, on the GW server, only on my IP address (192.168.0.200)._ I don't want it to affect the whole network.

Thanks a lot everyone,

---

### Post by walidch on 2011-04-18
*Bump*

---

