---
title: "problem with the network, probably the proxy"
date: 2012-04-10
forum: Server Platforms
---

### Post by rivh on 2012-04-10
Networking problem


I can not ping nowhere outside my network, I ping my gateway and my dns and all good. I'm setting the proxy as follows: export http_proxy = "http://148.229.1.6:3128". Also configure the proxy for apt in apt_conf file as follows: Acquire :: http::Proxy "http://148.229.1.6:3128" but nothing

 That may be missing. Help please

---

### Post by FreeD01 on 2012-04-11
Some routers block ping by default and also your proxy is probably protected by firewall which may block ping. It stops port scanning. No big deal, in most cases you do not need to ping out of your network.;)

---

