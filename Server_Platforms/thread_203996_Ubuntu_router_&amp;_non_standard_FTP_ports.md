---
title: "Ubuntu router &amp; non standard FTP ports"
date: 2006-06-26
forum: Server Platforms
---

### Post by nverhaar on 2006-06-26
Hey all,

I am using Ubuntu as a router/gateway/firewall machine at work, and we need to do regular FTP transfers to an external FTP on port 1111.

Anytime we try to do this, we are getting the following error from the FTP server:
426 Connection Closed.

From what I can gather, you must enable the ip_conntrack_ftp module to enable FTP access, however this only applies to port 21.

I have enabled the ip_conntrack_ftp module, and also given the client machine access to the outside world with the following:
iptables -t nat -A POSTROUTING -s 10.0.0.247 -o eth1 -j MASQUERADE

Does anyone know how I can enable the module to also work with port 1111, or is there another solution that will allow me to make connections to FTP's on non standard ports?

---

### Post by nverhaar on 2006-07-03
Hey all,

I wanted to investigate this situation further and determine if the problem occurs in other Linux distributions. I threw a copy of IPCop v1.4 on the same box, left all the defaults as they were and allowed MASQUERADING of all outbound traffic on ETH1.

Tried the FTP transfers again on port 1111 and had absolutely no problems.

Does anyone have any ideas as to what could be causing the 426 connection closed errors on Ubuntu? e.g. modules, routing table, sysctl settings, etc?

Any help would be appreciate guys!!

---

