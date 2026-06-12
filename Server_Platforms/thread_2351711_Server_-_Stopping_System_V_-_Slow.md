---
title: "Server - Stopping System V - Slow"
date: 2017-02-06
forum: Server Platforms
---

### Post by necpock on 2017-02-06
Hello, I have an issue with a VPS server. I believe it's running on XEN hypervisor. Upon issue of reboot command, the regular shutdown message happens but only after about 5-10 minutes, putty connection terminates and boot starts.
I decided to load a backup to a fresh install on a VB machine and now I can see that the delay is with "stopping system v runlevel compatibility".

After some furious searches, not many hints are cropping up about this on a non-gui server. I've trawled through the logs;

Dmesg only shows the message.
Nothing in lshw

Some have pointed to drivers but almost everyone experience no gui upon startup in desktop versions.

Any advice or hints would be duly accepted many thanks.

---

### Post by necpock on 2017-02-10
Solved the issue.... the delay was with fail2ban removing banned IP's from iptables before shutdown.

---

