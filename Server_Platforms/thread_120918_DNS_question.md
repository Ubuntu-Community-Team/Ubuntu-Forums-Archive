---
title: "DNS question"
date: 2006-01-23
forum: Server Platforms
---

### Post by vtec on 2006-01-23
I have a home network setup with a DNS server. Every thing works ok except it does not forward an address like "domain.com" to a defult adress "host.domain.com". For example with google you can go to [www.google.com](www.google.com) or google.com. Where is the setting for this in bind9.

---

### Post by drogoh on 2006-01-23
I assume you want something like this zone file snippet:

```

$ORIGIN domain.tld.
@      IN      A       1.2.3.4
www    IN      CNAME   @

```

Hope it helps.

---

### Post by vtec on 2006-01-24
That was it... Thanks. I remeber i did something like that a while ago but for the  couldn't remember what it was this time around.

---

