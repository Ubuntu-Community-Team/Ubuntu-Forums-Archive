---
title: "how to send signal from user space to kernel module"
date: 2014-08-02
forum: Ubuntu Application Development
---

### Post by zerop2 on 2014-08-02
how to send signal from user space to kernel module

---

### Post by tgalati4 on 2014-08-02
There are several frameworks that you could use:

```
man dbus-daemon
```

What specifically are you trying to do?

If you are simply trying to change a module switch then you would need to unload the module, change the switch and reload the module.

```
modinfo nameofmodulethatyouaretryingtochange
```

---

