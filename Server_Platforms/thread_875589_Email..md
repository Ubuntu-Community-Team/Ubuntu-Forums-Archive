---
title: "Email."
date: 2008-07-31
forum: Server Platforms
---

### Post by davidshq on 2008-07-31
I have sendmail installed (just using Webmin) so that PHP can send emails. I'd like to make sure (a) no one else can use it (e.g. open relay) and (b) how I can more effectively configure it to ensure message delivery.
David.

---

### Post by windependence on 2008-07-31
To check for open relay [http://www.abuse.net/relay.html](http://www.abuse.net/relay.html)

You should really think about installing postfix (no need to uninstall your sendmail) since sendmail is notoriously difficult to configure and also isn't the most secure mail software out there either. Postfix is a drop in replacement for sendmail, so that means you don't need to change anything that would normally work with sendmail, like your PHP configuration, it should just work.

-Tim

---

### Post by davidshq on 2008-07-31
Thanks. I'll take a look at Postfix and abuse.net.
David.

---

