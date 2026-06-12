---
title: "VMWare Server always needs reconfig after restart"
date: 2007-03-12
forum: Server Platforms
---

### Post by othomas_uk on 2007-03-12
**EDIT: **Just found the solution - check whether a file called "not_configured" is in /etc/vmware.  If it is, delete it.  The (re)configure script does not always remove it

Have installed the latest version of VMWare Server on Ubuntu 6.10 with no problems and it runs fine.  That is until I restart the computer (the actual computer and not the virtual one) - when I try and run VMWare Server again, it says it need to be (re)configured with /usr/bin/vmware-config.pl.

Have tried this as both regular user and root and every time I restart the actual computer I need to reconfigure vmware server.

Any ideas?

Owen

---

