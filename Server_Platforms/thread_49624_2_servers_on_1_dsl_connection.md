---
title: "2 servers on 1 dsl connection"
date: 2005-07-17
forum: Server Platforms
---

### Post by doc_holiday on 2005-07-17
Hello,

What I would like to do is run 2 web servers on 1 dsl connection (x.dyndns.org and y.dyndns.org). But because they are on the same connection they have the same public IP. Is there a way to route this traffic to the server I want.
I know boxes that can do it (Radware - linkproof and netscreen SSL) but I'm looking for this as home use.

Thanks

---

### Post by kirsche on 2005-07-17
I'd suggest to use apache and configure virtual servers.

---

### Post by farao on 2005-07-23
There is also the possibility of Pound ([www.apsis.ch)](www.apsis.ch)). It really works magic, and you can even redirect url-calls to a completely different location (handy when you use a backup server in a friends house for example). Pound makes it real easy to run every service you want behind port 80 (even vnc, just reroute vnc.domain.tld:80 to internal.ip-address:5900).

Best, Farao

---

