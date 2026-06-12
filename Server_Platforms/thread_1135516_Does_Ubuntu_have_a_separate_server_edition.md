---
title: "Does Ubuntu have a separate server edition?"
date: 2009-04-24
forum: Server Platforms
---

### Post by vfclists on 2009-04-24
Does Ubuntu have a separate server edition, or is it the  ubuntu-8.04.1-server-i386.iso?

I installed it using debootstrap onto a coLinux VM and a lot of things were not installed.

Is it possible to specify an install configuration for apt-get or some other install utility to reinstall to the set configurations?

/vfclists

---

### Post by cdenley on 2009-04-24
> **vfclists said:**
> Does Ubuntu have a separate server edition, or is it the  ubuntu-8.04.1-server-i386.iso?

I installed it using debootstrap onto a coLinux VM and a lot of things were not installed.

Is it possible to specify an install configuration for apt-get or some other install utility to reinstall to the set configurations?

/vfclists

There is a server edition which is simply the standard ubuntu OS with a package configuration optimized for a server. The most obvious difference is server edition does not have a desktop by default. The ISO you mentioned does appear to be the server edition. You can select different configuration profiles after install with this command:
```

sudo tasksel

```

---

### Post by Maheriano on 2009-04-24
The .iso you mentioned is the server edition, it's on the main ubuntu.com homepage. After installing that on a server, you can either run apt-get commands from its own command line or you can SSH into it from another machine and run them remotely. But you have access to all the same repositories as the Desktop edition.

---

