---
title: "HOWTO : Enable TLS/1.1 on Firefox 23.0"
date: 2013-08-08
forum: Security
---

### Post by samiux on 2013-08-08
Firefox 23.0 is released and it supports TLS/1.1 but does not enable it by default.

You can enable it manually.  Please refer to [this link]("http://samiux.blogspot.com/2013/08/howto-enable-tls11-on-firefox-230.html").

Happy secure browsing!

Samiux

---

### Post by kurt18947 on 2013-08-08
Thanks for that, done!  I wonder how long it'll take banks, credit card companies, shopping cart services etc. to institute 1.1?

---

### Post by Hungry Man on 2013-08-09
Many websites have already implemented TLS 1.1/1.2. Browser support for algorithms still has a bit to go, but there's significant progress already.

---

### Post by CharlesA on 2013-08-09
> **Hungry Man said:**
> Many websites have already implemented TLS 1.1/1.2. Browser support for algorithms still has a bit to go, but there's significant progress already.

How can you tell if your web server support TLS 1.1/1.2?

---

### Post by sandyd on 2013-08-09
> **CharlesA said:**
> How can you tell if your web server support TLS 1.1/1.2?

i dont have access to my buildserver atm so i cant check if its supported in current version of nginx, but it should
set ssl protocols to
```

ssl_protocols TLSv1.1 TLSv1.2 TLSv1 SSLv3;

```
in nginx vhost - that enables TLS 1,1.2,1.3 & SSL3

then test with ssllabs [https://www.ssllabs.com/ssltest/](https://www.ssllabs.com/ssltest/)

---

### Post by CharlesA on 2013-08-09
Looks like I need to add a line to my config files. Thanks!

---

