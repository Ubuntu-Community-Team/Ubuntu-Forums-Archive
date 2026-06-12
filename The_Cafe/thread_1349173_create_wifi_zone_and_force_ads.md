---
title: "create wifi zone and force ads"
date: 2009-12-08
forum: The Cafe
---

### Post by vinboy on 2009-12-08
hi
does anyone know how to create a wifi zone? and upon connection, the client must visit my website before he/she can use the internet?

thank you

---

### Post by the yawner on 2009-12-08
What you're looking for is a captive portal. I've explored a couple of solutions some months back. One is CoovaChilli which last I checked has a deb package. However, last I tried it, it required a bit tweaking since it requires a user/pass before allowing redirected users to browse. Then there's monowall/pfsense, Free-BSD firewall distros that provide basic captive portal features.

---

### Post by pwnst*r on 2009-12-08
> **vinboy said:**
> hi
does anyone know how to create a wifi zone? and upon connection, the client must visit my website before he/she can use the internet?

thank you

a DD-WRT compatible router (i suggest linksys) has these features.  here's just one example:  [http://www.dd-wrt.com/wiki/index.php/NoCatSplash](http://www.dd-wrt.com/wiki/index.php/NoCatSplash)

[DD-WRT main site]("http://www.dd-wrt.com/site/index")

---

