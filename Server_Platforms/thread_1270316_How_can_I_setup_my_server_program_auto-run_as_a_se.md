---
title: "How can I setup my server program auto-run as a service when startup?"
date: 2009-09-19
forum: Server Platforms
---

### Post by mrmrcc on 2009-09-19
How can I setup my server program auto-run as a service when startup? Thanks in advance!!

---

### Post by openfly on 2009-09-19
You need to learn to use init.d/

Or you could hide it somewhere in another startup script.  Biggest issue to be aware of is run levels and how scripts execute in each of them.

Not sure if ubuntu rocks an /etc/rc file.  Some do support it as a legacy startup script.  It's the easiest to interface with, but you'd learn a lot and be a better person for learning how init.d scripts are called and written.

---

### Post by Rob_H on 2009-09-19
Take look at the man page for update-rc.d. It will help you set up the necessary links to your startup/shutdown script.
```
man update.rc.d
```

---

