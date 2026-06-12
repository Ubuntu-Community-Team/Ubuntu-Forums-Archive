---
title: "My Apache is hijacking LAN requests"
date: 2009-03-10
forum: Server Platforms
---

### Post by vnevoa on 2009-03-10
There's a crazy problem in my home LAN. Timed out URLs end up being satisfied by my home server's Apache. :-k

Setup:
- WAN interface: Motorola cable modem;
- WAN Firewall/bridge: Sitecom off-the-shelf WiFi+Eth router; It forwards WAN port 80 to the Ubuntu box.
- LAN+WAN server: Ubuntu 8.04 server (Apache + Samba + SSH) wired to router (eth0), with dynamic DNS client;
- The Dynamic DNS service is configured for wildcard resolution (anything like *.mydomain.dyndns.com ends up forwarded to my cablemodem's/router's IP).
- LAN DHCP+DNS is provided by Sitecom router;
- The Ubuntu server has a second wired connection (eth1) and acts as a bridge for a special machine behind it; it serves DHCP+TFTP+DNS+AOE to this interface alone (although I may have made some mistake there).

Problem: 
Whenever an external URL is called in the LAN by the laptops and is not satisfied within reasonable time (like in a dead link), the Apache on my local server replies to that bad request by serving the standard "It works" page!!!...

I thought that the Ubuntu's DNScache was bleeding into the LAN, so I uninstalled it but the problem remained.
Only when I stop the Apache service the laptops have the expected behavior: they time out and give the normal "not found" browser response for bad URLs.
This is a serious problem because it can be very easily triggered; all it takes is a valid external Web server taking a bit longer to reply, and there goes my local server jumping into the conversation.

Anyone has a hint for me? How the heck does the local Apache trap external URLs???

Thanks.

---

