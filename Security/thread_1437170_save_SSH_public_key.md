---
title: "save SSH public key"
date: 2010-03-23
forum: Security
---

### Post by ryanfx on 2010-03-23
Hello all,

I am doing a small programming project and I need to be able to save the public certificates issued by servers (SSH) but I can't seem to figure out how to do this either in C or using linux tools.

Note I *don't* need the fingerprint, I need to save the certificate itself, is there any tool that can take care of this?

---

### Post by ryanfx on 2010-03-23
ssh-keyscan [host]

does exactly what I needed - enjoy =P

---

