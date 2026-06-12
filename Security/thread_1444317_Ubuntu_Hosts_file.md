---
title: "Ubuntu Hosts file"
date: 2010-04-01
forum: Security
---

### Post by iggy pop on 2010-04-01
Is it possible to configure the Ubuntu Hosts file in order to block any sites a user may regard as undesirable from contacting you? If so, how? Thanks

---

### Post by kerry_s on 2010-04-01
yeap, i use a hosts block list(mvp).

just open /etc/hosts as root(gksudo) and add your lines.

---

### Post by iggy pop on 2010-04-01
Thanks for the reply kerry_s

---

### Post by i.r.id10t on 2010-04-01
The hosts file will control what your computer can connect to, not how others connect to yours...

---

### Post by mikewhatever on 2010-04-01
Shouldn't you be looking at /etc/hosts.deny?

---

