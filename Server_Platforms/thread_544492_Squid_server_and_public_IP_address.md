---
title: "Squid server and public IP address"
date: 2007-09-06
forum: Server Platforms
---

### Post by Dexterp37 on 2007-09-06
Hi,

I've got my Ubuntu Box running Squid 2.6 perfectly, without any problem. That's part of my network configuration:

User PCs -> Router (Internet Gateway) -> ISP

Some user's PC have public IPs assigned to them. My router redirects all HTTP traffic (port 80) to my ubuntu squid machine (which is a different box from the router), in order to speed up user browsing experience if content is already caching (I'm trying to cache youtube streamings too).

Proxy is already transparent (users do not have to set IPs in their browsers in order to browse), and correctly not detected by Proxy Detectors, but I need to show user's IP address instead of router's one when going to some sites such as "whatismyipaddress.com". 

Is there any way to allow that?

Thank you

---

