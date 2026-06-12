---
title: "CACert.org certificate not trusted"
date: 2008-03-28
forum: Server Platforms
---

### Post by leohart on 2008-03-28
I have installed ca-certificates package on my Ubuntu server. However when I try to use openssl to test the certificate

openssl s_client -connect myserver.here:443 -showcerts

Neither was my certificate nor CACert.org certificate was verified and trusted. Am I missing something?

Both the Cacert.org website and Ubuntu package info say that Cacert.org is in the list of trusted root CA when installing ca-certificates package.

---

