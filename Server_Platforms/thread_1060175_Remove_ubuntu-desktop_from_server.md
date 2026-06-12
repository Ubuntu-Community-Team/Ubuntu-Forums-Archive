---
title: "Remove ubuntu-desktop from server"
date: 2009-02-04
forum: Server Platforms
---

### Post by carbm1 on 2009-02-04
I previously installed ubuntu-desktop on a 8.04 Server. I needed a GUI but I really didn't want all the extras... I would now like to go ahead and completely remove all the packages that were installed at that time.  It seems I can't just run...

```
sudo apt-get remove ubuntu-desktop
```

It doesn't remove all the extra packages. Anybody know of a good way to accomplish this?

---

### Post by ajgreeny on 2009-02-04
I'm not 100% sure, but I think ```
sudo apt-get autoremove ubuntu-desktop
``` should work as the **man apt-get** says it removes all dependencies.  You may, however need to reinstall **ubuntu-desktop** first for it to work at all.

---

### Post by cdenley on 2009-02-04
> **ajgreeny said:**
> I'm not 100% sure, but I think ```
sudo apt-get autoremove ubuntu-desktop
``` should work as the **man apt-get** says it removes all dependencies.  You may, however need to reinstall **ubuntu-desktop** first for it to work at all.

"sudo apt-get autoremove" removes all packages which were previously installed as dependencies, and not explicitly selected by you. I'm not sure how the desktop packages are marked in the package database for a desktop install. You can try "sudo tasksel", though, then deselect "ubuntu-desktop".

---

