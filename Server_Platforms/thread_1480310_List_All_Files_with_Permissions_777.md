---
title: "List All Files with Permissions 777"
date: 2010-05-11
forum: Server Platforms
---

### Post by craigp on 2010-05-11
how can i find all of the files on the server with permissions 777?

---

### Post by terazen on 2010-05-11
According to "man find" this should do it.
```
sudo find / -perm 777
```

---

### Post by craigp on 2010-05-12
well that was easy.. thanks a lot

---

