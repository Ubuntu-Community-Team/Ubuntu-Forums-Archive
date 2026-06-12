---
title: "NIS fails"
date: 2008-07-22
forum: Server Platforms
---

### Post by john.hall on 2008-07-22
When I boot the client, ypcat passwd doesn't work.  But if I do /etc/init.d/nis restart and then run ypcat passwd it works.  Why doesn't it get it right the first time?  

Webmin says it is supposed to start, and it's in /etc/rc5.d as S18nis.

Edit: Bind (on the server) is doing something similar.

---

