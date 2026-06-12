---
title: "postfix ,relay auth, from address"
date: 2012-06-21
forum: Server Platforms
---

### Post by SlugSlug on 2012-06-21
Using an non-auth smtp relay works fine.

setting up a smtp relay that needs authentication results in the from address (either via sendmail, or web forum software) being my authentication username inside /etc/postfix/sasl_passwd

Forum software is set to send the from address as donotreply@


Am I missing something?

---

### Post by SlugSlug on 2012-06-22
I should also mention that due to postfix not being able to do smtps I need to use stunnel

cat stunel.conf

```
client = no
foreground = no
pid = /var/lib/stunnel4/stunnel4.pid

[smtps]
accept = 5000
connect = smtp.virginmedia.com:smtps
```

---

### Post by SlugSlug on 2012-06-26
bump :(

---

