---
title: "How do I see what ports are available?"
date: 2009-09-18
forum: Security
---

### Post by mrcoulson on 2009-09-18
I would like to change SSH port to something besides 22.  Is there a way to display what ports are being used so I can choose one that is not in use?

Jeremy

---

### Post by x3roconf on 2009-09-18
Try: ```
sudo lsof -i
``` :)

---

### Post by i.r.id10t on 2009-09-18
netstat -tapn

Also, look at /etc/services since it lists default ports for many services...

---

### Post by mrcoulson on 2009-09-18
Excellent!  Perfect!  Thanks a ton!

Enthusiastically,
Jeremy

---

