---
title: "Samba, executed under what user?"
date: 2009-03-12
forum: Server Platforms
---

### Post by asimons999 on 2009-03-12
Ubuntu 8.10: What OS user is Samba executed under?

---

### Post by askreet on 2009-03-17
The main process is run as root.  However, when a user connects Samba will spawn a subprocess that is running as that user, in most situations.

I think Guest access continues to run as root, but I am not sure.

---

