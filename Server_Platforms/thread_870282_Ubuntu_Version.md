---
title: "Ubuntu Version?"
date: 2008-07-25
forum: Server Platforms
---

### Post by swu on 2008-07-25
I'm upgrading an app on my 6.06 LTS server and the upgrade notes say to check which version you are up to:

<< UBUNTU6 - Ubuntu Server 6.06.1 LTS >>

So how do I check what version of 6.06 LTS I have? What CLI will tell me this?

Thx!

---

### Post by bab1 on 2008-07-25
Try```
lsb_release -a
```

---

### Post by swu on 2008-08-01
That worked like a charm. Thx!

---

### Post by StickyStyle on 2008-08-01
Also, ```
$cat /etc/issue
```

---

