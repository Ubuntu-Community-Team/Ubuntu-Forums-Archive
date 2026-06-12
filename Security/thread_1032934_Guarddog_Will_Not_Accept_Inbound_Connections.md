---
title: "Guarddog Will Not Accept Inbound Connections"
date: 2009-01-06
forum: Security
---

### Post by pcox3921 on 2009-01-06
I am running ubuntu 8.04 Server as small office router/firewall that will not accept any inbound connection.   Internal network consists of W2K3 server and assorted WinXP clients and VoIP interface   Router/firewall will allow connections between internal clients and server (file sharing, FTP and PPTP VPN.  As such, the W2K3 server config and GuardDog zone config should be OK.  However, the router/firewall will not accept any connection from the net, thru the firewall and to the W2K3 server.  WhatIsMyIp.org open port scanner shows all ports (including FTP, SSH, PPTP) all with timeout.

GuardDog has W2K3 server zone set to allow protocols (FTP, PPTP, SSH) from the internet zone.

internal clients can FTP and make VPN connections out thru the router.

I am confused why ALL inbound ports seem to be closed.  I have PING enabled for all zones, but PING is blocked.

Any suggestions will be appreciated.

---

### Post by bodhi.zazen on 2009-01-06
Can you please clarify what you are trying to do exactly. Are you using your guraddog box as a router / firewall or do you have a separate router ?

How do you know it is a problem with guarddog ? Can you connect if you inactivate gruaddog ?

If it is guarddog you will need to give us more details on your configuration.

---

### Post by eatberrys on 2009-01-06
Yes more information would be very helpful. will it work with out Gaurddog in place?? have u made any recent changes to configuration or added to your network in a way that would effect this?? Have u ran Nmap on your outside ip?

---

### Post by pcox3921 on 2009-01-07
Network Config below:

Comcast Cable Modem  < > Ubuntu Firewall/Router < > Internal Network (W2K3 server, WinXP clients, VoIP adapter).

The network (both inbound and outbound connections) ran fine with a Linksys WRT54G router in place.  Unfortunately, the network has outgrown the capabilities and thruput of the WRT54G V8 router/access point.  

The Ubuntu router/firewall replaced the WRT54G.  Ubuntu server is providing DHCP services for internal lan.  ISP is providing DNS services (The DHCP server is passing the DNS server addresses from teh ISP thru to the DHCP clients).  No changes made to the W2K3 server, the internal LAN clients or the VoIP adapter.  W2K3 server and VoIP LAN interface are configured as DHCP.  Ubuntu DHCP server is configured to provide static IP address to the MAC address for the W2K3 server and VoIP adapter.

I am using Guidedog to configure router and Guarddog to configure IP tables.  GuideDog is managing NAT/router functions (GuideDog does not have any ports forwarded).  GuardDog is managing the firewall functions.

GuardDog Firewall/IPtable configuration appears to be working correctly as the firewall controls access between resources on the internal network.  Certain LAN clients cannot access the internet, certain clients cannot access the VoIP adapter, etc.

Brief Guarddog config listed below:

Zones:

Internet (default with GuardDog)
Local (Default with GuardDog)
LAN
VoIP
Server

Protocols served by Internet to Local, LAN, server and VoIP zone:

DNS
HTTP
HTTPS
PPTP
FTP
PING
NTP

Protocols served by Internet to VoIP Zone:

SIP (UDP 5060 - 5061)
RTP (UDP 10000 - 20000)
TFTP

Protocols served by Server to LAN Zone

NetBIOS (for Windows file sharing)
FTP (for testing server configurationj)
PPTP (for testing server configuration)

Protocols served by Server to Internet Zone:

FTP
PPTP
PING

Protocols served by LOCAL to LAN

SSH
FTP
NFS

Advanced config for GuardDog has DHCP client set for ETH0 (interface to COmcast Cable Modem) and DHCP server on ETH1 (interface to internal LAN).

I have not run Nmap from inside lan on external IP. (will do tonite)

System was initially tested using Firestarter to manage router/firewall (on same Ubuntu server).  Network functioned  correctly for both inbound and outbound connections.  However, Firestarter is limited in ability to create/manage complex networks.  Guarddog seems to be better solution as network grows.

I hope this info helps.

---

### Post by eatberrys on 2009-01-07
From what it sounds like its defently a configuration error with Gaurddog I have not used Gaurddog before thou. Have you tryed makeing an allow all rule with it and seeing if u can get thou ?

What ports were open when u ran nmap ?

You most likely need port forwarding to access services such as ftp from the internet side of the server

---

