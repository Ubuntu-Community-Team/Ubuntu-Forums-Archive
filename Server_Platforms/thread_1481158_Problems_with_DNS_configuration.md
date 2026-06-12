---
title: "Problems with DNS configuration"
date: 2010-05-12
forum: Server Platforms
---

### Post by nsantibanez on 2010-05-12
Hi,

Have a problem with Ubuntu server 8.04, not recognize a name server example: server.test.cl

the name what resolv is test ...

first modify the file configuration hosts and before modify the hostname with the command: hostname server.test.cl

please help me!

---

### Post by jjcv on 2010-05-13
Not 100% sure what you mean.  However to set up your system to use a nameserver you need to edit 

/etc/resolv.conf

There should be a line like this:

nameserver  xxx.xxx.xxx.xxx

where xxx.xxx.xxx.xxx is the IP address of the nameserver.

---

### Post by nsantibanez on 2010-05-14
> **jjcv said:**
> Not 100% sure what you mean.  However to set up your system to use a nameserver you need to edit 

/etc/resolv.conf

There should be a line like this:

nameserver  xxx.xxx.xxx.xxx

where xxx.xxx.xxx.xxx is the IP address of the nameserver.
Hi men, thanks for your help.

this problem is a view dns in my dns server, only a one configuration of external access, not a configuration of internal access.

Thanks!

---

