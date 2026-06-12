---
title: "Mqueue - Mailq lost"
date: 2008-04-01
forum: Server Platforms
---

### Post by ChrisPols on 2008-04-01
Hi,

I'm trying to find the mqueue folder to see the outgoing emails currently in the system.

Everywhere else on linux, it seems to be in /var/spool/mqueue , however with ubuntu, this does not seem to be the case.

Could someone tell me where this folder is or what name it's called?

If I run mailq / sendmail -bp I get 1800 messages, so there are mails there.

any ideas?
Thanks
Chris

---

### Post by uncannybuzzard on 2008-04-03
```
cd /
find ./* -name mqueue
```

---

