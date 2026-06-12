---
title: "system monitor extension dependency"
date: 2024-04-23
forum: Ubuntu Development Version
---

### Post by Claus7 on 2024-04-23
Hello,

I noticed that there is a relatively new extension under system extensions named system monitor. Trying to enable it, it showed an error about gtop library. So I opened synaptic package manager and installed gir1.2-gtop-2.0 along with libgtop2-dev, exited and logged back in, in order to make it work.

Regards!

---

### Post by jbicha on 2024-04-23
Please file a bug against gnome-shell-extensions now. There may be time to get this fixed before the Ubuntu 24.04 LTS release.

---

### Post by Claus7 on 2024-04-23
Hello,

> **jbicha said:**
> Please file a bug against gnome-shell-extensions now. There may be time to get this fixed before the Ubuntu 24.04 LTS release.
done: [https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extensions/+bug/2063267](https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extensions/+bug/2063267)

Regards!

---

### Post by corradoventu on 2024-04-24
Fix released, now it works.

---

