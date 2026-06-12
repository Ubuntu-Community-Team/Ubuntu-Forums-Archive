---
title: "Firefox krb5 authentication"
date: 2013-01-18
forum: Security
---

### Post by myronx on 2013-01-18
Hello all,

I've problem with Kerberos authentication in Firefox included in Ubuntu. I've correctly configured Apache with krb5 module and tgt generated for user on workstation. When I'm using chromium-browser (with --auth-server-whitelist=my.domain parameter) on this workstation, everything works fine. Firefox installed on Windows workstation also is using Kerberos authentication. But it looks, that Firefox built-in Ubuntu does not try using Kerberos (there is no request for ticket to HTTP service). I've set network.negotiate-auth.trusted-uris=my.domain (I also tried .my.domain - with leading dot), but it isn't working.

I've tested it on Ubuntu 10.04 (32bit) and 12.04 (64bit).

---

