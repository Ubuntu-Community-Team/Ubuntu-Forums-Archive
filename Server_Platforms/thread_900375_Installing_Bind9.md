---
title: "Installing Bind9"
date: 2008-08-25
forum: Server Platforms
---

### Post by chrislynch8 on 2008-08-25
Hi,

I'm trying to install bind9 and I get the following error.

```
sudo aptitude install bind9 bind9-doc nscd

```

The last two items install with no issues and the bind9 then give me this message.

```
Setting up bind9 (9.3.2-2ubuntu1.5)...
md5sum: /etc/bind/named.conf: No such file or directory
md5sum: /etc/bind/named.conf.local: No such file or directory
```

In the /etc/bind folder I only have the rndc.key and none of the config files.

Rgds
Chirs

---

