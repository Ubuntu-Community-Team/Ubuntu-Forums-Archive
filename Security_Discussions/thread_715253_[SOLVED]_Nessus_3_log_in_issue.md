---
title: "[SOLVED] Nessus 3 log in issue"
date: 2008-03-04
forum: Security Discussions
---

### Post by wormser on 2008-03-04
I have Nessus 3 installed on Gusty.  I am unable to log onto the Nessus server.  During the set up I created the first user with nessus-add-first-user and also nessus-mkcert

> It was not possible to log in using the supplied credentials

Any ideas?

---

### Post by wormser on 2008-03-04
I got it solved!

Start nessusd:

```
sudo /opt/nessus/sbin/nessusd start
```

Start the client:  Applications> Internet> Nessus Client.

Then click Connect> select localhost> Edit> enter in the correct Login and Password> Save> Connect.

---

