---
title: "Settings for high traffic servers"
date: 2009-07-27
forum: Server Platforms
---

### Post by dragos2 on 2009-07-27
What kind of tuning do you guys apply for 1000+ simultaneous connections/second
to a webserver? 

* sysctl tuning
* tcp/ip tuning (by default I don't think it will accept more than 1024 conections/process - net.core.somaxconn)
* ulimit tuning


I really appreciate every answer. 


Thanks

---

### Post by snek on 2009-07-27
Quite interrested in this one as well, so far I'm having to maintain pre-installed CentOS servers for work but want to eventually move to Ubuntu when we order new servers.
If I can tweak them to surpass the CentOS servers in performance I'm sure work would be very happy :)

---

