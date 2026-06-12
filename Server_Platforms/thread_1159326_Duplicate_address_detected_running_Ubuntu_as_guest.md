---
title: "Duplicate address detected running Ubuntu as guest on VMWare"
date: 2009-05-14
forum: Server Platforms
---

### Post by ivancruz on 2009-05-14
Environment:

Host is a Windows 2003 server running VMWare Server 1.0.8.
Guests are two Ubuntu 9.04 Server. Both guests using bridged
networking. Hosts and guests in a /27 subnetwork.

Network: xxx.xxx.xxx.128
Netmask: 255.255.255.224
Gateway: xxx.xxx.xxx.129
IP range: xxx.xxx.xxx.130 to xxx.xxx.xxx.158

Windows Host IP: xxx.xxx.xxx.133
1st. Ubuntu IP: xxx.xxx.xxx.135
2nd. Ubuntu IP: xxx.xxx.xxx.136

Problem:

1st. Ubuntu guest installs and works flawlessly but the second one always record "eth0: duplicate address detected" on syslog when interface is brought up. Network does not works during installation also (language packs are not downloaded).

Already tried many other available IPs on our range and got the same result.

Any ideas?

Ivan.

---

### Post by ivancruz on 2009-05-14
Solved!!!

Duplicated address was HMAC and no IP. Solved after forcing HMAC with hwaddress parameter on /etc/networking/interfaces and rebooting.

---

