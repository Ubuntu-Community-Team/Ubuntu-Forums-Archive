---
title: "VMware Tools install failed"
date: 2008-03-26
forum: Virtualisation
---

### Post by russjar on 2008-03-26
Hi,

I have just upgraded my VMware Workstation build to the latest version 6.0.3 build 80004.

I tried to upgrade the vmware tools in a ubuntu guest and I am getting the error;

+root@BrowserOnly:/tmp# rpm -hiUv VMwareTools-6.0.3-80004.i386.rpm +
error: Failed dependencies:
/bin/sh is needed by VMwareTools-7241-80004.i386

What gives?

Cheers

---

### Post by dcstar on 2008-03-26
> **russjar said:**
> Hi,

I have just upgraded my VMware Workstation build to the latest version 6.0.3 build 80004.

I tried to upgrade the vmware tools in a ubuntu guest and I am getting the error;

+root@BrowserOnly:/tmp# rpm -hiUv VMwareTools-6.0.3-80004.i386.rpm +
error: Failed dependencies:
/bin/sh is needed by VMwareTools-7241-80004.i386

What gives?

Cheers

```
whereis sh
ls -al /bin/sh
```

---

