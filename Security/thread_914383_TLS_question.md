---
title: "TLS question"
date: 2008-09-08
forum: Security
---

### Post by themostunoriginalname on 2008-09-08
If I have the most updated SSL library in the repository, what version of TLS do I have?

---

### Post by MBoelen on 2008-09-09
dpkg -l | grep -i tls

Could possible give you more info about your version.

Or try connecting with the s_client mode within OpenSSL (openssl s_client -debug)

---

