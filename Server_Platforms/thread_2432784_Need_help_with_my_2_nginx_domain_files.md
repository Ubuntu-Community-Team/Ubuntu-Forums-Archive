---
title: "Need help with my 2 nginx domain files"
date: 2019-12-08
forum: Server Platforms
---

### Post by Heeter on 2019-12-08
>>>

---

### Post by TheFu on 2019-12-09
Doubt I can help.  My nextcloud install doesn't run on the same system as my SSL termination.
The nextcloud system runs apache with a 40 line config file and HTTP only.
The nc.example.com reverse proxy+ssl termination runs nginx with a 94 line config file just for nextcloud.  Anyway, hope those config file line counts give you an idea for what is needed.

There were some other changes to the nextcloud config (I think it was in the php settings) needed to have URLs forced to be HTTPS even with HTTP-only on that machine.

I'd tried to setup an apache security module, but it broke nextcloud apps.

Also, the nextcloud security scanner always fails because it doesn't see the HTTPS front-end, so that is where is complains and fails, always.

Neither the reverse-proxy nor the nextcloud server are available over the internet. Both require using a VPN to access.  SSL helps privacy, not security.

Getting let's encrypt keys was a hassle initially, until I started ignoring all the web servers and used acme.sh in standalone mode to get certs.  My reverse-proxy setup isn't only for nextcloud. Have about 15 other websites also doing similar things. Most are internal use only and also require using the VPN to access from the outside.

See how this isn't all that useful to you? Sorry.

---

