---
title: "SSH: what's the difference between RSAAuthentication and PubkeyAuthentication?"
date: 2013-04-08
forum: Security
---

### Post by user201304 on 2013-04-08
(These are settings in /etc/ssh/sshd_config )

---

### Post by cool110 on 2013-04-08
RSAAuthentication is for SSHv1 keys
PubkeyAuthentication is for SSHv2 keys

---

### Post by kevdog on 2013-04-10
These might be what the settings are in the sshd_config file - but I think both can use either RSA or DSA style keys.  Do a wikipedia search on RSA and DSA -- these represent the mathematical model on how the keys were constructed.

---

