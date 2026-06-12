---
title: "KVM, Monitor on Telnet,&amp; netcat"
date: 2010-12-03
forum: Virtualisation
---

### Post by YorYor on 2010-12-03
Hi all, hoping another who has tried the above combination could share some experience.

I run my KVM virtual machines by hand/command line, typically with -monitor telnet:127.0.0.1:5800,server,nowait

I then use netcat to issue commands to it, such as system_reset, system_shutdown etc etc.

The one thing I've not been able to do, and have to fall back on regular telnet, is to get the monitor's output, such as info status or info whatever.
```
root@machine:# echo "info status" | nc localhost 5800
root@machine:# 
```

Has anyone managed to script commands to the qemu monitor and still be able to get the output it generates?

---

