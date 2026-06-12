---
title: "Xen unable to access domU console"
date: 2010-03-11
forum: Server Platforms
---

### Post by kunix on 2010-03-11
I'm running Ubuntu Hardy as a dom0 for my 4 Debian Lenny domU systems.
Xen version is 3.3.0 + xen-tools 3.8.
Everything was going smoothly so far but a few days ago I decided to stop the SSH service on one of the domU's. Then I tried to 
```
xm console
```
to my machine and found that I was unable to login.
After rebooting the domU I've monitored the boot process to the point it stopped at

```
Starting file alteration monitor: FAM.
Starting Hardware abstraction layer: hald.
Starting periodic command scheduler: crond.
Starting web server: apache2.
[   21.537465] ip_tables: (C) 2000-2006 Netfilter Core Team
```

I have the 
```
extra = "console=xvc0 xencons=xvc0"
```
in the domU's config file.

Please help me with this one, I've locked myself out from my machine :(

---

