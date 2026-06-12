---
title: "Disable Root Login Warning Gutsy"
date: 2008-02-16
forum: Security Discussions
---

### Post by Tsarevich on 2008-02-16
I am using Ubuntu Gutsy and I want to remove the warning - this session is runnng as a previledged user. How to disable this? I am not logging in as root but I would still like to know! I know this is a big security risk. But this can save time when I do want to login as root!

---

### Post by astrotech226 on 2008-02-16
You just need to set a root password.

```
sudo passwd
```

After you change the root password, you can do things like "su -" and actually log in as root.

---

