---
title: "resolve gnump3d to hostname"
date: 2007-08-06
forum: Server Platforms
---

### Post by reckless2k2 on 2007-08-06
is it possible to use a hostname such as:

music.domain.com

that would automatically resolve to port 8888 used for gnump3d?

i'm not sure if this is possible. i currently have apache setup and am using virtual hosts successfully with other hostnames but i'm trying to figure out if i can get a hostname to redirect to a port like 8888.

thanks.

---

### Post by reckless2k2 on 2007-09-04
i was able to resolve this issue with mod_proxy for apache if anyone is interested. now i can hit url music.domain.com and it will "redirect" to domain.com:8888.

---

### Post by arrrghhh on 2007-09-09
well how'd ya do it?  i'm curious.

---

### Post by reckless2k2 on 2007-09-10
i run a mail server using zimbra and they had a tutorial about running their http host and a normal apache host on the same port using mod_proxy:

[http://wiki.zimbra.com/index.php?title=ZimbraApache](http://wiki.zimbra.com/index.php?title=ZimbraApache)

obviously i catered it to my situation and was successful.

---

