---
title: "DNS udp floods (overflow ?) - how to protect ?"
date: 2009-11-16
forum: Security
---

### Post by Salmus on 2009-11-16
Hello,

Starting from three days ago - my ubuntu dns servers started to freeze (1000 load) and reboot was the only option. 

I checked out the tcpdump logs:

```
01:02:13.553220 IP 211.161.46.84.27865 > 89.44.246.252.53: 61138 [1au] A? gshk.happy-host.com. (48)
01:02:13.553560 IP 202.98.224.69.6320 > 89.44.246.252.53: 45460% [1au] A? gshk.happy-host.com. (48)
01:02:13.557933 IP 211.161.46.85.15380 > 89.44.246.252.53: 18703 [1au] A? gshk.happy-host.com. (48)
01:02:13.558559 IP 219.146.2.35.26857 > 89.44.246.253.53: 63421 A? gshk.happy-host.com. (37)
01:02:13.558576 IP 61.153.177.179.56471 > 89.44.246.252.53: 17683% [1au] A? gshk.happy-host.com. (48)
01:02:13.558598 IP 61.31.233.5.57829 > 89.44.246.253.53: 45036 [1au] A? gshk.happy-host.com. (48)
01:02:13.559712 IP 61.220.8.35.33504 > 89.44.246.253.53: 1030 [1au] A? gshk.happy-host.com. (48)
```


Almost 10kpps with the same query, spoofed IPs.


This queries put my dns servers down, with load at 1000 - and as I said - rebooting was the only option.

In config files, recursion is not allowed. Dns servers answers only for domains hosted. 


Bind is updated at the lastest version.



Any clues ? How can I stop this further attacks ? I've checked the issue and start flooding myself - with spoofed IPs -- servers got 400 load in approximately 3 minutes. 


Thank you !

---

### Post by __p1n__ on 2009-11-16
Put in an iptables rule for local port 53 with a limiting rate.

---

