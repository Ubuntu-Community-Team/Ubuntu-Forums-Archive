---
title: "Kernel driver is not accessible to current user."
date: 2008-08-12
forum: Virtualisation
---

### Post by Ezlo4 on 2008-08-12
So first I had the problem of not having the kernel driver installed but now it says I don't have write permissions.

Help please.

---

### Post by theyranos on 2008-08-12
Context, please. Is this post related to [this thread](http://ubuntuforums.org/showthread.php?t=887772)?

If so, try this command (replacing yourname with your username): 
```
sudo adduser *yourname* vboxusers
```

If it says it's successfully added you to the vboxusers group, give VirtualBox another try and see if it works.

---

