---
title: "BIND9 Forwarding Issue"
date: 2012-05-11
forum: Server Platforms
---

### Post by masterJanky on 2012-05-11
So, I'm having an issue with a BIND9 implementation.  I have configured the server to cache entries and pointed everybody on my guest wireless to this server.  I can see the entries in the cache, but whenever a new DNS request comes in, the request is forwarded upstream every time (I verified with wireshark).  Anybody run into this?

---

### Post by nsnidanko on 2012-05-11
check if your /etc/resolv.conf has only localhost as its nameserver (should be 127.0.0.1). Also check if the forwarded request are not for expired records.

---

