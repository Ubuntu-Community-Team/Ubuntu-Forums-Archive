---
title: "can't install .deb packages"
date: 2014-03-30
forum: Ubuntu Development Version
---

### Post by willygatti on 2014-03-30
I'm currently testing the Ubuntu 14.04 beta, and whenever I try to install software from a .deb package downloaded from the web, I get an error message stating, ```
package operation failed the installation or removal of a software package failed.
```  How do I install .deb packages such as Google Chrome and Ubuntu Tweak sucessfully in Ubuntu 14.04 beta?

---

### Post by Mateusz Stachowski on 2014-03-30
Inability to install external packages with Ubuntu Software Center is a [bug]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1290228").

You can install .deb packages from terminal with this command:

```
sudo dpkg -i deb package
```

---

### Post by ajgreeny on 2014-03-30
Or if you want a gui install gdebi; it's much faster and I think bertter than USC.

---

