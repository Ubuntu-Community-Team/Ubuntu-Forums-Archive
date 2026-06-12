---
title: "Setting Up NIS Password Complexity Rules"
date: 2006-03-01
forum: Server Platforms
---

### Post by SuperMike on 2006-03-01
Anyone know how to set up NIS password complexity rules on Ubuntu?

---

### Post by nocturn on 2006-03-02
Just add cracklib to pam (it works for all mechanisms).

But I would like to really recommand against using NIS if you can avoid it.  Your passwords are transmitted over the network in cleartext....

---

