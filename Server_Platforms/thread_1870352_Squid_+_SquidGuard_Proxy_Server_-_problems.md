---
title: "Squid + SquidGuard Proxy Server - problems"
date: 2011-10-27
forum: Server Platforms
---

### Post by chrislynch8 on 2011-10-27
Hi,

I have a couple of remote servers that are running Squid with SquidGuard for restricting Internet Access. I have an Internet Web application that is accessable Internally & Externally using Internet DNS and External DNS. Both Squid, SquidGuard & my Shorewall Firewall are configured the same way on two servers. But one server is driecting users out to the Public IP addrress and the other is using the Internal IP address for accessing the web app. 

Both servers have the exact same Internal DNS setting, both Server can ping the Internal Web App by name & IP address. But when running through squid one is always directing the users to the External address, forcing them to https which I do not want for Internal Access.

Any ideas as to why squid would not be using the servers DNS settings. On both sevres, dig tells me that it is using the Internal DNS, one the server causing the problem when I stop directing web access over squid they can access it using the Internal DNS then

Rgds
Chris

---

