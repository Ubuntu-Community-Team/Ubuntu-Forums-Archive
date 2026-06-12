---
title: "SSL Certificates from a CA for private servers?"
date: 2014-04-10
forum: The Cafe
---

### Post by PartisanEntity on 2014-04-10
**Background:**

I maintain a private owncloud server that I use for syncing contacts, calendar, firefox sync, and files between my various applications and devices.

I also use it to share files with family and friends.

So far I have been using self signed certificates. At one point I had forced all traffic to the server to go through SSL, but I got tired of explaining to non-technical family members and friends that it was OK to ignore the warning in the browser about the self signed certificate.

**Question:**

Personally I would love to turn back on the SSL enforcement on the server, and so that got me thinking about perhaps buying a SSL certificate. Any issues I am missing?

Thanks.

Until now the price put me off, but I just found an offer on GoDaddy for about €50 per year, which I think is pretty affordable.

What are your opinions? Pros and cons for private individuals buying certificates?

---

### Post by Lars Noodén on 2014-04-10
The signing certificate should probably be kept offline and used only on an air-gapped machine.  That'll mean an extra machine + backups even if it is just a netbook.

---

