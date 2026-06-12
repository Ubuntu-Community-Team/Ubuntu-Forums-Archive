---
title: "Bandwidth Throttling for LAN Users to the Internet"
date: 2013-09-24
forum: Server Platforms
---

### Post by qkazu on 2013-09-24
Hi everyone! I was wondering if you could point me in the right direction… My main problem is some people in my house like to use YouTube as their TV, and as everyone knows, that cripples everyone else's internet connection. I wanted to ask if you can suggest any linux-based software that can limit each user's bandwidth. Here's my current setup (my old office closed down so I was able to get the Cisco stuff for free):
> ISP Modem
[COLOR="#FFFFFF"]............[/COLOR]|
Cisco 1841 Router
[COLOR="#FFFFFF"]............[/COLOR]|
Cisco Catalyst 2960 Switch  -----------------------------------------------------------------
[COLOR="#FFFFFF"]............[/COLOR]|[COLOR="#FFFFFF"]................................................................................[/COLOR]|[COLOR="#FFFFFF"]........................................[/COLOR]|
Ubuntu 12.04 Server (Media Server)[COLOR="#FFFFFF"].................[/COLOR]Other PCs[COLOR="#FFFFFF"].................[/COLOR]Wi-Fi Access Point
I've been Googling stuff but all I keep on seeing is the Squid Proxy server. From what I've read, it speeds up internet access because it caches the data but I don't think that's what my home network needs. I've also seen some posts where ubuntu was used as the router with 2 NICs, but I really want to use the 1841 since I already have it anyway. Right now the 1841 is my LAN gateway. The ubuntu server currently has the Plex Media Server on it and I was thinking of putting the bandwidth throttling software on it (and maybe change my network setup to make it the gateway?).

I'm just starting out on Network/Server administration so I apologize in advance if I'm way off track. I just thought this could be a fun project and I could learn a few more stuff doing it. Thanks in advance!

---

### Post by CharlesA on 2013-09-24
You'd need to set up QoS on your network, but how to set it up usually depends on your router. I'm not that familiar with Cisco gear, but maybe [this]("http://www.cisco.com/en/US/docs/ios/12_2/qos/configuration/guide/qcfmcli2.html") will help.

---

### Post by qkazu on 2013-09-29
Thanks for the link. It's really helpful. I've been reading up on QoS as you said and it looks like I won't be able to keep the 1841 if I wanted to use QoS on ubuntu. I guess I'll just look for another ubuntu home project to work on. Thanks anyways!

---

