---
title: "Burst.NET VPS DNS Server"
date: 2010-08-11
forum: Server Platforms
---

### Post by richfearless on 2010-08-11
Hi Folks,

I am trying to setup a DNS server on my Burst.NET Ubuntu Setup.
This is my current ifconfig:


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4980 (4.9 KB)  TX bytes:4980 (4.9 KB)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:127.0.0.1  P-t-P:127.0.0.1  Bcast:0.0.0.0  Mask:255.255.255.255
          inet6 addr: ::1/128 Scope:Host
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:3904695 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3431504 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3142355406 (3.1 GB)  TX bytes:3107564671 (3.1 GB)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:<internet-ip1>  P-t-P:<internet-ip1>  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1

venet0:1  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:<internet-ip2>  P-t-P:<internet-ip2>  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1


Do you know if these meet the requirements for a DNS server?

Regards,
Rich

---

