---
title: "Squid transparent proxy can't start"
date: 2020-05-09
forum: Server Platforms
---

### Post by kventin on 2020-05-09
Hello. 
I've installed Ubuntu Server 20.04 LTS and Squid 4.10. Squid and Ubuntu have default configuration. Ubuntu Server is clran. If I use standard proxy Squid on port 3128, all works good. Configuration of Squid is standart. But if I change  http_port 3128 transparent or intercept in squid.conf, Squid can't start.

If I do "service squid status", I can see this error:
May 08 20:23:08 localhost squid[6095]: FATAL: mimeLoadIcon: cannot parse internal URL: [http://localhost:0/squid-internal-static/icons/silk/image.png](http://localhost:0/squid-internal-static/icons/silk/image.png)

How I can fix this error?

---

