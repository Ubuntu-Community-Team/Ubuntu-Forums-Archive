---
title: "OpenVPN and Iptables Question"
date: 2007-01-15
forum: Server Platforms
---

### Post by walker45 on 2007-01-15
Hi folks.  I am currently setting up an OpenVPN server on my Samba server so I can securely access my files while I'm away; maybe even do some gaming :)  

I setup the VPN server on Ubuntu Server 6.10 as a bridged VPN.  The server is behind a firewall/gateway (IPCop) that i was planning on using to forward traffic from the internet (port 6233) to my vpn server.

I have successfully installed and configured the VPN server, now I am working on configuring Iptables.  While doing so, I thought of a question about security.  

When you connect to a VPN, you can push all traffic through the VPN using the redirect traffic option however, what I wanted to do was be able to connect to the VPN so that i can access files from the Samba server, while having all other traffic (web surfing, e-mail, etc.) go through the regular, non-vpn connection. Is it possible to safely implement the above? Would the Iptables rules below provide enough security for this setup?

Thanks for any advice.
walker45

Iptables Rules:
```

#Allow SSH 
iptables -A INPUT -p tcp -i eth0 --dport 1112 -j ACCEPT

#Allow HTTP
iptables -A INPUT -p tcp -i eth0 --dport http -j ACCEPT

#Allow Samba/WINS
iptables -A INPUT -p tcp -m tcp --dport 137:139 -j ACCEPT
iptables -A INPUT -p udp -m udp --dport 137:139 -j ACCEPT

#Allow OpenVPN
iptables -A INPUT -p udp --dport 6233 -j ACCEPT

#Allow traffic to/from bridged interfaces
iptables -A INPUT -i tap0 -j ACCEPT
iptables -A INPUT -i br0 -j ACCEPT
iptables -A FORWARD -i br0 -j ACCEPT

#Allow Loopback
iptables -A INPUT -i lo -j ACCEPT

#Allow Estiblished Connections
iptables -A OUTPUT -m state --state NEW -o eth0 -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -m state --state NEW -o eth0 -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

#Log Packets and Drop
-A INPUT -j LOGNDROP
-A LOGNDROP -p tcp -m limit --limit 5/min -j LOG --log-prefix "Denied TCP: " --log-level 7
-A LOGNDROP -p udp -m limit --limit 5/min -j LOG --log-prefix "Denied UDP: " --log-level 7
-A LOGNDROP -p icmp -m limit --limit 5/min -j LOG --log-prefix "Denied ICMP: " --log-level 7
-A LOGNDROP -j DROP
```

---

