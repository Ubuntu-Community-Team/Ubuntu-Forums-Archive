---
title: "Postfix problems with smtp_tls_policy_maps"
date: 2008-12-07
forum: Server Platforms
---

### Post by froggy42 on 2008-12-07
Hi,

I will try to do TLS encryption with mails to a customers domain. So I've setup smtp_tls_policy_maps. Everything works fine so far!

But:
Mails which could not transferred through an TLS channel as defined in smtp_tls_policy_maps become deferred instead of bounced?

How can I change this behaviour?

Dec  6 11:47:17 srv-s141 postfix/smtp[18288]: D7226814E:
to=<i...@xxx.de>, relay=mailin.rzone.de[81.169.145.100]:25,
delay=81151, delays=81151/0.05/0.17/0, dsn=4.7.4, status=deferred (TLS
is required, but was not offered by host mailin.rzone.de
[81.169.145.100])

Thanks for any suggestions?

CU Marc

---

