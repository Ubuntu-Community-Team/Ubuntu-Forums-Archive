---
title: "apt-get upgrade vs apt-get dist-upgrade"
date: 2008-03-20
forum: Server Platforms
---

### Post by xsystemx on 2008-03-20
Configured a Ubuntu server and I am trying to figure out if my cron job should be apt-get upgrade or apt-get dist-upgrade?

What are the differences between upgrade and dist-upgrade?

Which one is best for a server?

---

### Post by justin whitaker on 2008-03-20
> **xsystemx said:**
> Configured a Ubuntu server and I am trying to figure out if my cron job should be apt-get upgrade or apt-get dist-upgrade?

What are the differences between upgrade and dist-upgrade?

Which one is best for a server?

Apt-get upgrade is useful for general maintenance. It looks at what is installed on your system, and updates it with the latest patches, etc. 

Dist-upgrade is useful when you are going from release to release because it does dependency checking along the way.

---

### Post by az on 2008-03-20
apt-get upgrade will upgrade the package versions on your system when a newer version is available.  It still does dependency checking and will skip upgrading a package in the case of a conflict.

apt-get dist-upgrade will be able to remove packages in favor of other, higher priority packages.  Both use the package manager so they both use package dependencies.  You can run dist-upgrade for regular server maintenance if you want.

Unless you change your sources.list, both should behave the same.

---

### Post by netlogic on 2008-03-21
> **xsystemx said:**
> Configured a Ubuntu server and I am trying to figure out if my cron job should be apt-get upgrade or apt-get dist-upgrade?

What are the differences between upgrade and dist-upgrade?

Which one is best for a server?

```
apt-get update && apt-get upgrade -y
```

just run it as a root

---

