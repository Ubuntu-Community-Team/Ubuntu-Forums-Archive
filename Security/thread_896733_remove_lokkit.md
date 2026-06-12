---
title: "remove lokkit"
date: 2008-08-21
forum: Security
---

### Post by heiNey on 2008-08-21
i tried to remove lokkit, by doing 'sudo apt-get remove lokkit' and it says that it's been removed, but its still running whenever i boot up.  do i need to manually remove every file with 'lokkit' on it?

---

### Post by cariboo on 2008-08-21
In a terminal type:

```
sudo /etc/init.d/lokkit stop
```

Then in the same terminal type:

```
sudo apt-get purge lokkit
```

Jim

---

