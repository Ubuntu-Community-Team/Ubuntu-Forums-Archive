---
title: "OpenVPN ZzZZzzZZ &gt;_&lt;!!"
date: 2008-12-24
forum: Server Platforms
---

### Post by sinclair86 on 2008-12-24
I have an open vpn server (172.16.0.1) running on my hardy server (192.168.2.1). When I vpn in from my local network on another computer I am able to ping the vpn server 172.16.0.1. When i vpn from a remote terminal i can only ping the client (172.16.0.6) and not the vpn server (172.16.0.1). I am assuming this is a routing issue(?) but it looks right to me =\. Yes I have portforward the vpn on my router. Disable the firewall (for testing). Any help would be great.

---

### Post by neomaximus2k on 2008-12-26
well i'm unsure but we had a similar problem but with windows, we changed the dns server ip on the client machine to the ip of the server and it then worked.

---

### Post by windependence on 2008-12-26
Your VPN clients cannot be on the same network as the LAN clients. For example if your network is 172.16.0.0, then your clients should be on something like 10.0.0.0 or 192.168.0.0. OpenVPN will take care of the routing. You could also have them on say 172.16.2.0, as long as it's different.

[http://www.informit.com/articles/article.aspx?p=605499](http://www.informit.com/articles/article.aspx?p=605499)

[http://www.thebakershome.net/openvpn_tutorial](http://www.thebakershome.net/openvpn_tutorial)

This is the best way to do it by installing pfsense, completely configurable from a web GUI:

[http://pfsense.nsa.co.il/tutorials/openvpn/pfsense-ovpn.pdf](http://pfsense.nsa.co.il/tutorials/openvpn/pfsense-ovpn.pdf)



-Tim

---

### Post by sinclair86 on 2008-12-27
Yea I figured it out. The OpenVpn tehy have in the repos is 2.1rc-something and the the windows was using 1.0.9 I glanced somewhere when i was trying to figure this issue out is that they arent really backwards compatible so I installed the newest one on both machines and it worked... lol

---

