---
title: "Encrypting SSH host keys?"
date: 2008-06-05
forum: Security
---

### Post by Artis on 2008-06-05
Is it possible to encrypt SSH host keys so that a password is requested at the SSH server startup?

---

### Post by Dr Small on 2008-06-05
Generally you are prompted with a password anyhow, if you use sudo.
```
sudo /etc/init.d/ssh start
```

---

### Post by Artis on 2008-06-05
> **Dr Small said:**
> Generally you are prompted with a password anyhow, if you use sudo.
Right, that doesn't mean that the keys are encrypted however...

---

### Post by Dr Small on 2008-06-05
Correct. You could however encrypt the host keys with GPG, and then edit the init.d script to decrypt the keys before it starts SSH.

---

