---
title: "VirtualBox and VENOM?"
date: 2015-05-22
forum: Security
---

### Post by peter_smith4 on 2015-05-22
Today an update to VirtualBox was available on my Ubuntu 12.04 system. The update fixes CVE-2015-3456 (VENOM).

By default no floppy controller is added when creating a new VM in VirtualBox. Does this mean that it was not possible to exploit the security hole in Virtualbox, unless a floppy controller was added to the VM?

For the last couple of days I have been trying to get a clear overview on how VirtualBox was affected by VENOM, but almost no information could be found.

---

### Post by TheFu on 2015-05-22
No - you need the patch even if you don't attach a FDC. Redhat has a nice write-up for why.
BTW, some sample code was created  which demonstrates this issue.  It is about the FDC code being available regardless of whether is was requested.

---

