---
title: "openvpn connection"
date: 2018-05-07
forum: Server Platforms
---

### Post by sniper8752 on 2018-05-07
I am trying to vpn into my server with openvpn.  It is not working.  The error log shows that the connection is timing out.  I allowed for the traffic on the port (iptables), inbound on my outer interface, so I am not sure why it wouldn't be getting through.  I did a netstat -tulpn, and got this: 
```
udp        0      0 0.0.0.0:1194            0.0.0.0:*                           1084/openvpn
```
A nmap scan shows that the outside and inside interfaces do not have port 1194 open, which seems contradictory to this.  I am not sure where to go from here.

My rule: ```
-A INPUT -i eth0 -p udp -m state --state NEW -m udp --dport 1194 -j ACCEPT
```

---

### Post by wildmanne39 on 2018-05-07
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by darkod on 2018-05-07
1. Is the server directly on the internet (public IP) or behind a router? If it is behind a router you have to allow and forward the port on the router too.

2. Please show all iptables rules because the one you posted is not enough in some cases (if you tried closing off your server too much):
```
sudo iptables -L -n -v
```

---

