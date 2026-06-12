---
title: "[SSH] Avoid that SSH send informations about its own version number"
date: 2010-11-28
forum: Security
---

### Post by andy4560 on 2010-11-28
Hi,

thi is my first message on this forum...

I need an information about OpenSSH configuration...

I noticed that one of the few informations that OpenSSH server sends not encrypted is its number version and info about the operating system.

How can I configure OpenSSH to avoid that these informations are sent ?

Could I manage this kind of presentation message of the server, for example deciding what has to be written?

Thank you for every suggestion!

---

### Post by HermanAB on 2010-11-28
```
$ man sshd
```

---

