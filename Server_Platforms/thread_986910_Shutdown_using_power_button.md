---
title: "Shutdown using power button"
date: 2008-11-19
forum: Server Platforms
---

### Post by arasush on 2008-11-19
Hi,
We use Ubuntu Server 8.04.
This server is mostly used as a file server - we typically don't login into this server at all - even through ssh.
Is it possible to configure the server to shutdown when the hardware power button is pressed - from the command line login prompt?

Thanks!

---

### Post by arasush on 2008-11-19
My bad that I didn't search properly before posting the question.

[http://ubuntuforums.org/showthread.php?t=913410&highlight=Shutdown+power+button](http://ubuntuforums.org/showthread.php?t=913410&highlight=Shutdown+power+button) has a solution.

Just need to install acpid:

```
sudo apt-get install acpid
```

---

