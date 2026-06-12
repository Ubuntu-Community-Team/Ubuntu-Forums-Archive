---
title: "how to ping between guest os when on different subnet mask"
date: 2010-04-04
forum: Virtualisation
---

### Post by ambarishpathak on 2010-04-04
i have installed virtualbox on ubuntu 9.10 host. on host i have 2 ports eth0 and eth1 with ip 192.16.9.67 and 192.168.9.67 respectively.
i have installed two guestos and setup a bridge connection between them. for 1st guest os g1 i have assigned ip 192.16.9.1 with default gateway 192.16.9.67 and 2nd g2 with ip 192.168.9.10 with default gateway 192.168.9.67 .

After doing this i am not able to ping between guest oss and neither host form guest os and vice-versa.

can someone suggest, what is the problem or how to solve this?

---

### Post by dcstar on 2010-04-05
> **ambarishpathak said:**
> i have installed virtualbox on ubuntu 9.10 host. on host i have 2 ports eth0 and eth1 with ip 192.16.9.67 and 192.168.9.67 respectively.
i have installed two guestos and setup a bridge connection between them. for 1st guest os g1 i have assigned ip 192.16.9.1 with default gateway 192.16.9.67 and 2nd g2 with ip 192.168.9.10 with default gateway 192.168.9.67 .

After doing this i am not able to ping between guest oss and neither host form guest os and vice-versa.

can someone suggest, what is the problem or how to solve this?

Firstly, 192.16.9.x is a public IP range, you should **not** be using it unless you own it.

Secondly, unless you have ipforwarding set up on your host - or a router on your network - then the packets will not be forwarded.

---

