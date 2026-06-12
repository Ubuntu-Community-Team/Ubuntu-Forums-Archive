---
title: "Nginx proxy."
date: 2012-02-18
forum: Server Platforms
---

### Post by jailbait on 2012-02-18
I currently have two nginx installations - one on the gateway and one on the server in the internal network.
I use the gateway nginx installation to route ipv6 to the internal LAN, because I haven't managed to figure out how to setup ipv6 properly.

Since I use virtual hosts on the server nginx, its resulted in quite a weird configuration.

On the gateway, I have to map all the sites to their respective internal server IPs in /etc/hosts, and get nginx to proxy through the site itself.

I.E.: add carlie.com to /etc/hosts with the internal server ip, then point the gateway nginx towards carlie.com

Is there any alternate way to do this?

---

