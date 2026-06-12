---
title: "connect two networks"
date: 2018-11-03
forum: Server Platforms
---

### Post by chawas on 2018-11-03
I have a sever connected to internet access point through usb and an eth1 connected to another outside network. How do I configure so that I get internet at  the same time always accessing the external network

---

### Post by TheFu on 2018-11-03
Set the priority for which connection should be used, when, in the routing table.  This is commonly controlled via the "metric" number.  A metric can be set for every different routing subnet.  

If you need more details, then we need to know your level of networking knowledge, which release you are running (things are different in different releases), and both the current routing table and the desired routing table.  Being abstract doesn't really work so much. Be exact and detailed.

Please.

Welcome to the forums.

---

### Post by darkod on 2018-11-03
What is the "another outside network"? Is it a network with private subnet or a public subnet?

You would usually have single access to the internet and that would be your default gateway at the same time. For other networks connected to other interfaces with private subnet, you do not set a gateway and the OS knows to send traffic destined for that subnet to that interface.

---

