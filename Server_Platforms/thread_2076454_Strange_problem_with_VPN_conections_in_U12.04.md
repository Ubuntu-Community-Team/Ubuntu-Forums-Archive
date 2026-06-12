---
title: "Strange problem with VPN conections in U12.04"
date: 2012-10-26
forum: Server Platforms
---

### Post by kyniu1 on 2012-10-26
Hi All,
The action plan of U12.04 assumed to make a gateway for the computers in the network (network Comps have different Windows).
I have two eth, I instaled iptables + ip_forwarding, dhcp server and dnsmq. No samba on it.
Computers in LAN see the internet, WWW, FTP - all is working fine.
There is only a small problem. I have a Microsoft SBS 2003 server in colocation which is placed VPN.
So far, computers were connecting with this VPN without any problem (set to 200 simultaneous VPN connections). 
When all traffic began to go through U12.04 only one connection could be established from LAN to VPN (if I turn off U12.04 all VPN connections fork fine)
When one computer is connected to VPN through U12.04, on the rest computers I have an error "800VPN or remote connection failed and the tunnel has not been matched."
Have any of you had the chance or know where he can be the reason?
Kyniu

---

