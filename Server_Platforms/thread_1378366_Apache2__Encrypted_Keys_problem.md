---
title: "Apache2 / Encrypted Keys problem"
date: 2010-01-11
forum: Server Platforms
---

### Post by dj_lightning on 2010-01-11
It looks like the server.key was encrypted when this server was installed.  Anytime apache tries and start its asks for a pass to load the server.key.  Anyone have might shed some light on which is the best way to fix this?

Thank you

```
Apache/2.2.8 mod_ssl/2.2.8 (Pass Phrase Dialog)
Some of your private key files are encrypted for security reasons.
In order to read them you have to provide the pass phrases.
```

---

### Post by wirelessmonkey on 2010-01-11
The only thing you can do without the password is generate a new keypair.

---

