---
title: "VB in 11.10-add user to vbusers"
date: 2011-09-03
forum: Virtualisation
---

### Post by tajreed on 2011-09-03
Need to add user to vbusers group for USB to work. How can I do that? They seemed to have removed users/groups from 11.10.

---

### Post by CharlesA on 2011-09-04
Open a terminal and run this:

```
sudo usermod -a -G vboxusers username
```

---

### Post by tajreed on 2011-09-04
That did it. Thanks

---

