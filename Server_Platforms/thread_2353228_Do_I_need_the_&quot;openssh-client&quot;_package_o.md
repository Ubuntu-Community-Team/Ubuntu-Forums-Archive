---
title: "Do I need the &quot;openssh-client&quot; package on my server?"
date: 2017-02-20
forum: Server Platforms
---

### Post by PrinceVince on 2017-02-20
It appears that the **openssh-server** package installs **openssh-client** as a dependency. Is the latter necessary on a server that only gets logged into, but doesn't itself log into other SSH hosts?

---

### Post by wildmanne39 on 2017-02-20
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2017-02-20
Probably not but as it is installed as dependency by apt-get I would say it doesn't hurt leaving it... Besides, maybe in the future you will use ssh client connections from that server.

---

