---
title: "What happens when you lose ssh connect while doing a process?"
date: 2010-03-11
forum: Server Platforms
---

### Post by bakegoodz on 2010-03-11
I was shelled into my remote webserver from my laptop, and I lost my wireless connection while installing Mysql. Should I expect broken packages, or would it finish without me connected?

---

### Post by n0dix on 2010-03-11
No, the process doesn't continue. It's aborted. But don't worried MySql and all Databases know what to do in this cases. This mean, the databases may continue in a consistent form: all tables, data, etc. are not lost.

---

### Post by gmargo on 2010-03-11
If you're using an SSH terminal login (not a VNC session), then you could use **screen(1)** to maintain a logged-in instance on the remote system.

---

