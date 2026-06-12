---
title: "ssh and bind"
date: 2006-11-10
forum: Server Platforms
---

### Post by fremlins on 2006-11-10
I have a couple of questions (in fact serious security concerns) about ssh and bind on ubuntu.

When I install the openssh-server packag, root logins are allowed. Yet this is not a recommended option. In fact on FreeBSD/Solaris/and no doubt others, the default is PermitRootLogin  set to "no". Why is this set to "yes" by default on ubuntu?

When I install the bind package, it doesn't create a specific user although, for example, openntpd does. In fact, bind runs as root. It is recommended to run bind with least privilege. So, why is this not so on ubuntu?

I realise these are not part of the core install on ubuntu, but they are ubuntu packages.

---

