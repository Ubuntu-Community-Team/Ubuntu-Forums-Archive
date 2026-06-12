---
title: "Fowarding Ports To Different Server?"
date: 2009-04-24
forum: Server Platforms
---

### Post by kevin11951 on 2009-04-24
I would like it so that if port 631 (for example) is requested, ubuntu server (9.04) will forward it to a different server (eg. 192.168.2.204)

---

### Post by BkkBonanza on 2009-04-24
You can do this with ssh every easily. I'm not sure precisely what you want but a simple port forward can be handled with,

**ssh -L 631:locahost:631 user@192.168.2.204 -N**

This may be close but not perfect so you should dig into the ssh manual, **man ssh**. There are quite a few tutorials on "ssh proxy" as well using google that may help. There's also dynamic and reverse proxies using ssh as well so one of all these options will work.

---

