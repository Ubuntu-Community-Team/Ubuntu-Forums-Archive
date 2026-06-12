---
title: "Postfix Instance (chrooted) and SASL authentication (via postgres)"
date: 2014-06-11
forum: Server Platforms
---

### Post by gb10hkzo-fb on 2014-06-11
Has anyone successfully implemented the above config ?  I'm really struggling and would appreciate any generous config sharing :D

(I've tried everything, and yes the sasl mux is in the chroot directory, and no, nothing of use is coming up in the logs which just makes it more frustrating)

(As an alternative, has anyone managed to get this working [http://wiki2.dovecot.org/HowTo/DovecotPostgresql](http://wiki2.dovecot.org/HowTo/DovecotPostgresql)..... in a Postfix instance ?)

---

### Post by gb10hkzo-fb on 2014-06-11
never mind, got it working using [COLOR=#333333][FONT=Helvetica]courier-authdaemon instead.[/FONT][/COLOR]

---

