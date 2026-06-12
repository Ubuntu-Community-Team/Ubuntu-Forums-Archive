---
title: "Auto-enable proxy ARP?"
date: 2006-06-10
forum: Server Platforms
---

### Post by TimP on 2006-06-10
Is there a way to enable proxy ARP for an network interface device on system boot? In /etc/network/options I don't see anything about proxy_arp and I tried adding net/ipv4/conf/eth0/proxy_arp=1 and net.ipv4.conf.eth0.proxy_arp=1 in /etc/sysctl.conf but that didn't seem to do it. Is there a configuration file that controls this or should I just add a script to /etc/network/if-up.d?

Thanks!

---

