---
title: "Setting up OpenPGP for Launch pad."
date: 2008-09-02
forum: Security
---

### Post by moluv83 on 2008-09-02
Sorry for the n00b question but i'm trying to send my pgp key to the ubuntu server how do i get this done?  Thanks in advance.




-"Almost Micro$oft free" \\:D/

---

### Post by loell on 2008-09-02
in seahorse you can just sync and publish key in its remote menu.

---

### Post by moluv83 on 2008-09-02
> **loell said:**
> in seahorse you can just sync and publish key in its remote menu.

Once I get to the add keyserver what do i put for host and port?

---

### Post by Dr Small on 2008-09-02
From the command line:
```
gpg --send-keys --keyserver keyserver.ubuntu.com <KEY-ID>
```

---

