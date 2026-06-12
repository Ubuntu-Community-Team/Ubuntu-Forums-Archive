---
title: "Key C1289A29 not found"
date: 2010-04-02
forum: Ubuntuzilla
---

### Post by jasp1 on 2010-04-02
When I try to follow the instructions at [http://ubuntuzilla.wiki.sourceforge.net/]("http://ubuntuzilla.wiki.sourceforge.net/") on adding the package signing key to my keyring, I get a "not found" error:

```
$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpgkeys: key C1289A29 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
```

---

### Post by nanotube on 2010-04-03
just tried it, it works for me... maybe it was a glitch on the keyserver, give it another try?

---

### Post by jasp1 on 2010-04-07
> **nanotube said:**
> just tried it, it works for me... maybe it was a glitch on the keyserver, give it another try?

Yep, it works for me now too.  Thanks.

-Jay

---

