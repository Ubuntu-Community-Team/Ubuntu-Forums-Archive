---
title: "Delete IPv6 link local address permanently?"
date: 2007-06-22
forum: The Cafe
---

### Post by prabin on 2007-06-22
Hi all,

I am facing some problem related to IPv6 Link local Address

if i type the command 
>ifconfig eth0

It shows 

eth0 Link encap:Ethernet HWaddr 00:13:D3:3F:7F:37 
inet addr:172.16.170.117 Bcast:172.16.170.255 Mask:255.255.255.0
inet6 addr: fe80::213:d3ff:fe3f:7f37/64 Scope:Link <- here
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:205560943 errors:0 dropped:0 overruns:0 frame:1
TX packets:742535676 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:515791587 (491.8 MiB) TX bytes:3168788086 (2.9 GiB)
Interrupt:193 

Now inet6 addr : fe80::213:d3ff:fe3f:7f37/64 is deleted by ifconfig command

and when it type the following linux commands 
> ifconfig down
> ifconfig up

fe80::213:d3ff:fe3f:7f37/64 appeared once again

how link local address fe80::213:d3ff:fe3f:7f37/64 can deleted permanently?

---

