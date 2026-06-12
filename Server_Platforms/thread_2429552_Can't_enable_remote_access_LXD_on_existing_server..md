---
title: "Can't enable remote access LXD on existing server."
date: 2019-10-19
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2019-10-19
I just reconfigured my desktop to hold my running containers if I need to do something with the main server however now I cannot enable remote access on the server. I've done the core.https trust password and port configs but this is what I get. I've restarted the LXD service.

```

lxc remote add megalith megalith.mylan.home

Error: Get https://megalith.mylan.home:8443: Forbidden
```

Server

```
lxc config showconfig:
  core.https_address: 192.168.1.2
  core.trust_password: true
```

Same problem with

```
core.https_address: '[::]:8443'
```

I currently have access from the server to my desktop but not the other way around. I'd like both ways if possible. I'm hoping that I don't need to move all my running containers to the desktop so I can run lxd init again on the server.

---

