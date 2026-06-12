---
title: "certificates: thunderbird complains about common/domain name mismatch"
date: 2009-04-15
forum: Server Platforms
---

### Post by randomstuff on 2009-04-15
I have a postfix/dovecot combination serving several different domains. When using thunderbird it keeps complaining that the Common Name in my self-signed certificate does not match the domain name.

Can/Should I create different certificates for each domain, specifying a different Common Name in each of them?

Or should I use the actual FQDN of the server as common name, and set thunderbird to use the FQDN as the mailserver name? This would likely work, but it would be nicer if each domain could simply use mail.mydomain.com as mailserver.

What is the preferred way of handling this issue?

---

