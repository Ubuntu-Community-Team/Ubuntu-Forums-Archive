---
title: "Route all traffic over ppp0"
date: 2012-06-24
forum: Server Platforms
---

### Post by coupas on 2012-06-24
What I have:

 A server running 12:04, connected to a router. The router connected to an ADSL modem.

 The server has 192.168.1.2 as local ip on eth0. The rest of the network is the same: 192.168.1.xx.

 In the server, I have also configured a VPN client that I can call and get an ip assigned. The connection goes by the name ppp0

 What I want:

 I

 Be able to log in over ssh or vnc on my server, it runs headless and start up the VPN connection and a firewall. All internet traffic will then go on ppp0. If the VPN connection disconnects so, no internet traffic may be permitted. Only traffic from 192.168.1.xx should then be allowed. So I can log on, turn off the firewall, dial ppp0 and restart the firewall.

 Is this something that can be done relatively easily?

 Thank you thank you in advance for the help that can be offered concerning this.

---

