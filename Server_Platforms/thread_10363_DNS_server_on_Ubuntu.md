---
title: "DNS server on Ubuntu"
date: 2005-01-07
forum: Server Platforms
---

### Post by nocturn on 2005-01-07
I'm considering replacing my current server with Ubuntu.
It is hosting a DNS server for my local domain and a caching DNS server (resolving both my local domain and external DNS).

I migrated away from bind to djbdns for security reasons and I became to love djbdns for the simplicity of administrating a zone.  Yet this is not free software (free to use but restricted).

Is there any free software that can replace this (available on Ubuntu)?
I'm looking for both the primary DNS function as the caching, but two sperate packages of OK (as long as they handle the work).

Thanks.

---

### Post by node on 2005-01-07
Don't see what s wrong with Bind :)

---

### Post by nocturn on 2005-01-07
[QUOTE=node]Don't see what s wrong with Bind :)[/QUOTE]

It has a very bad track-record in security, and maintaining a zone is more complex then it needs to be.

Once you are used how djbdns does this, bind looks horrible.

---

