---
title: "IPv4 foward security"
date: 2011-06-11
forum: Server Platforms
---

### Post by linuxuser123456 on 2011-06-11
[FONT=&quot]Hello[/FONT]
  
  [FONT=&quot]I have an OpenVPN(10.04.2 LTS) server running in bridge (TAP) mode. It’s sitting behind a router and then a cable modem. The VPN works perfectly but I have a security concern. In order to allow the VPN clients to connect to the internet, I had to enable IPv4 forwarding on the server. Is this is a security hole?  Can a hacker access my server’s connection from the internet (without authenticating with OpenVPN) and access my network. Can someone use Ipv4 forwarding to access my LAN network from the WAN

[/FONT]   [FONT=&quot]I used this command to enable ipv4 forwarding[/FONT]
  [FONT=&quot]echo 1 > /proc/sys/net/ipv4/ip_forward[/FONT]
  
  [FONT=&quot]Without IPv4 forwarding my VPN clients can only access my LAN and router, but they cannot reach my modem or the internet.[/FONT]
  
  [FONT=&quot]  ..VPN server..............router(w/NAT).................modem(w /NAT)         ...............internet[/FONT]
  [FONT=&quot]192.168.20.120-----192.168.20.1----------------192.168.10.1----------------public IP[/FONT]
  [FONT=&quot]ipv4 forwarding.........port forward 1194............port forward1194[/FONT]
  
  [FONT=&quot]Is this is a good idea, or a security hole? Can someone explain to me what Ipv4 forwarding does?[/FONT]
  
  [FONT=&quot]Thanks[/FONT]

---

### Post by spynappels on 2011-06-13
As long as only port 1194 is forwarded, you should be ok. You can firewall it at the server level as well to only allow traffic from the VPN to be routed but not all.

My experience with OpenVPN is from running it in Routed mode rather than in Bridged, and IPv4 forwarding is required to allow packets from the VPN IPs to be routed to LAN addresses, I presume it will be similar on bridged mode, as the tunnel still uses it's own IP addresses, iirc.

---

