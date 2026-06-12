---
title: "drbd with hardy heron"
date: 2008-04-25
forum: Server Platforms
---

### Post by mang_ucup on 2008-04-25
I can't find Drbd latest package from repository in hardy heron.
Refer to Linbit and Ubuntu News, Hardy Heron integrates DRBD into its Server Edition.

[http://www.linbit.com/en/news/single-news/art/16/31/](http://www.linbit.com/en/news/single-news/art/16/31/)
[http://www.ubuntu.com/news/ubuntu-8.04-lts-server](http://www.ubuntu.com/news/ubuntu-8.04-lts-server)

I only can find drbd8-utils from the repository list. There is no drbd8-module-source like usually we can find it from ubuntu gutsy repository.

---

### Post by geertn on 2008-04-25
It's included in the kernel. You can just do: 
```
modprobe drbd
``` Add it to /etc/modules if you want to load it on startup.

For the userspace part you can install drbd8-utils.

---

