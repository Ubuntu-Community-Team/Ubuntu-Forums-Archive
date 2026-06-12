---
title: "dnssec-keygen not create zone key"
date: 2006-11-27
forum: Server Platforms
---

### Post by ArcticSnowman on 2006-11-27
Hi,

I've been trying to set up secure auto update of the DNS records by the DHCP server, however the majority of the howto's I've found tell me to use the following command to generate the TSIG key.

```
dnssec-keygen -a HMAC-MD5 -b 128 -n zone key-test
```

However on Ubuntu 6.10 I get the following response...

```
dnssec-keygen: a key with algorithm 'hmac-md5' cannot be a zone key
```

Does it matter if I go with '-n host' instead?

Steven

---

