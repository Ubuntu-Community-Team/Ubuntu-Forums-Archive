---
title: "iptables Forwarding and Squid (HTTP-HTTPS)"
date: 2015-12-08
forum: Security
---

### Post by rani2 on 2015-12-08
Hello Everyone...

I have trouble with squid and iptables port forwarding rules,
I installed Squid (HTTP and HTTPS) and it run fine...

I want some user from internet to access my local server in my local network,
I configure iptables with DNAT rules in PREROUTING, every time port 8089 accessed from internet, iptables will forward to my local server, and I already open used port in squid too,

Internet --- (eth0) (((Squid, iptables server))) (eht1) --- Local network

I try to access my iptables rule from my local network it fail too, Squid block my access and send message "Connection Refused"

please help me,
sorry for bad english

---

### Post by SeijiSensei on 2015-12-09
Squid isn't really designed to be a port forwarder.  It's primary purpose is to cache objects downloaded from the web.  Usually it just listens on port 3128, resubmits the requests it receives on that port out to the Internet, and passes the results back to the requesting client.

Your iptables rules should forward the inbound traffic ahead of any Squid-related rules.  Are you trying to reach a server behind the machine running Squid?   If so, did you enable packet forwarding in /etc/sysctl.conf by removing the hash mark from the line
```
net.ipv4.ip_forward=1
```
and rebooting?

---

