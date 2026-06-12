---
title: "Simple NAT traversal techniques"
date: 2014-04-14
forum: Ubuntu, Linux and OS Chat
---

### Post by Cubytus on 2014-04-14
Hi there, 

I intend to slightly modify a WD MyBook Live, very similar to Ubuntu since it runs Debian, by allowing it to automatically open ports to make it accessible from outside. It has *inadyn* configured to follow IP changes, but except for *miniupnp*, I am not aware of any simple NAT traversal techniques. More, while UPnP is widely implemented on consumer-level routers, some, perhaps more security-conscious, have it disabled by default. The MBL seems to run a proprietary UPnP mapping application, which is not documented thus can't read another configuration to map other ports (SSH and FTP).

So which choices would be best to traverse consumer-level combined NAT-firewalls? Of course it needs to rely only on standard software, so WD's client software is excluded.

---

### Post by TheFu on 2014-04-14
Use openvpn. Don't open any other ports. That is just asking for trouble, especially with unencrypted access.

---

### Post by Cubytus on 2014-04-14
Does it come with a server, that would be run on startup on the MBL, and clients for OS X and Ubuntu? Which side would initiate the connection? And more importantly, would the client be able to establish a connection as the MBL will be behind a firewall?

---

### Post by Cubytus on 2014-04-26
Still no answer? I read a bit about UPnP and its Apple counterpart, NAT-PMP. But as you point out, they're not very secure. Another page referred to this exact matter, namely accessing a MBL, but still requires manual port forwarding. There's also PCP, supposed to be more secure than the previous two, but the router has to support it, which isn't guaranteed.

How would openVPN, or any other solution, solve the issue of creating a tunnel to different machines without requiring manual ports config? And supported on any common router?

---

