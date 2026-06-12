---
title: "Dovecot with SquirrelMail"
date: 2011-03-30
forum: Server Platforms
---

### Post by walle1357 on 2011-03-30
Okay, so I am attempting to create a mail server on Ubuntu 10.10 using Dovecot, SquirrelMail, Sendmail, and Apache2 (for SquirrelMail), but I can't get SquirrelMail to connect to Dovecot. I get the error message: 
```

Error connecting to IMAP server: tls://localhost.
111 : Connection refused

```
from SquirrelMail.

Any ideas? I'm starting to get annoyed with Dovecot.
Thanks!

---

### Post by falko on 2011-03-30
Any errors in /var/log/mail.log?

What's the output of ```
netstat -tap
```?

---

### Post by SeijiSensei on 2011-03-30
Why bother with TLS when the IMAP and web servers are on the same machine?  Just use port 143 and standard IMAP.

---

