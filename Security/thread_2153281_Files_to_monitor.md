---
title: "Files to monitor"
date: 2013-06-10
forum: Security
---

### Post by toosweetnitemare on 2013-06-10
All,
I have been googling around for different guides on what files to monitor that people would edit for malicious intent. In my readings so far, i have found the common files people edit.
so far i have found:
[LIST=1]
[*]/etc/hosts
[*]ufw config files
[*]/bin/login
[/LIST]

what other files do you guys monitor actively and why?

Thanks in advance!
-tsnm

---

### Post by tgalati4 on 2013-06-11
/var/log/auth.log  What admin activities are taking place on the system.

---

### Post by toosweetnitemare on 2013-06-11
> **tgalati4 said:**
> /var/log/auth.log  What admin activities are taking place on the system.

would this be more for a file to watch what changes happen or one that no changes should happen to?

Thanks!

---

