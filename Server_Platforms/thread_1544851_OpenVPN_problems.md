---
title: "OpenVPN problems"
date: 2010-08-03
forum: Server Platforms
---

### Post by deb10er0 on 2010-08-03
Hi, 
sorry for my bad English.


I have a problem. I have tried so much, but nothing has worked.


[FONT=Verdana]My Network: [/FONT]
VPN-Server (Ubuntu, only VPN): 192.168.249.71 (IP firm, Port 1194 UDP firm)
Prim. DNS (there is a DHCP 192.168.249.100-199): 192.168.249.67
Sek. DNS: 192.168.249.73
Gateway: 192.168.249.1[FONT=Verdana]This works:
[/FONT]VPN-Server: [COLOR=#000000]Without changing the[/COLOR] server.conf (TLS and the keys has been adapted) 
Client: [COLOR=#000000]Without changing the[/COLOR] client.ovpn (TLS and the keys has been adapted)

Connection works (between server-client); Ping 10.8.0.1 works; Ping 192.168.249.71 works

Ping 192.168.249.xxx (another client) don´t work (it´s ok, because I haven´t change anything more).The VPN-Clients should be have the IPs between 192.168.249.230-240.
1. Is this possible? How?

The clients must also have access to network-drives and other clients.
2. Do I need a bridge?
3. If I don´t need a bridge, how can I solve this.

4. Would it go, if I install on my VPN server a DHCP server and assigns him the 230-240 range?

5. Can somebody help me please?deb10er0

---

### Post by spynappels on 2010-08-03
have you enabled client-to-client in the server conf file?

---

### Post by deb10er0 on 2010-08-03
Yes, I have.

Must I have a bridge?

Can I use the same network (192.168.249.0)?
Our intern DHCP uses 192.168.249.100-199 and I want to use the 230-240 IPs for VPN.

---

