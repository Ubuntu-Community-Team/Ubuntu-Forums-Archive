---
title: "Clearing auth.log"
date: 2009-01-28
forum: Security
---

### Post by hardysummer on 2009-01-28
How do I clear my auth.log? It would not allow me to overwrite with nothing (sudo echo "" > /etc/var/auth.log).

---

### Post by cdtech on 2009-01-28
Have you thought about using "logrotate" it helps keep your logs in order.

---

### Post by bettlebrox on 2009-01-29
Do this:

[INDENT]sudo bash
cat /dev/null > /etc/var/auth.log[/INDENT]

Then ctrl-d or exit to exit.

---

