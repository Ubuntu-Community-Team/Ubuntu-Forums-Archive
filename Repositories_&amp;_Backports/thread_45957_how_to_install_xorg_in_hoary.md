---
title: "how to install xorg in hoary?"
date: 2005-07-02
forum: Repositories &amp; Backports
---

### Post by cowlip on 2005-07-02
I try to upgrade x-window-system-core to Xorg, but apt-get says that it is kept back.  How do I upgrade it?

---

### Post by Xian on 2005-07-02
[QUOTE=cowlip]I try to upgrade x-window-system-core to Xorg, but apt-get says that it is kept back.  How do I upgrade it?[/QUOTE]
Please post the output of the following commands:
```
$ sudo apt-cache show x-window-system-core
$ sudo apt-get install x-window-system-core
```

---

