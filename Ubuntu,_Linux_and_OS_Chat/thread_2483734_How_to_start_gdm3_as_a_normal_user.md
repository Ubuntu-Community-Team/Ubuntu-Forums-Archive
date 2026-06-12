---
title: "How to start gdm3 as a normal user"
date: 2023-02-07
forum: Ubuntu, Linux and OS Chat
---

### Post by ishackigozi on 2023-02-07
when start the session using gdm, by launching /usr/sbin/gdm3. I get an error that Only the root can run GDM. Please advise.
This is on Ubuntu 22.04

---

### Post by TheFu on 2023-02-08
You cannot.  GDM requires root to provide login. It would be useless without it.

However, you can probably use sudo and restart the display-manager service.

```
sudo systemctl restart display-manager
```

---

