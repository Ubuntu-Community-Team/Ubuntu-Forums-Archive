---
title: "Installation error for lsp-plugins-jack-1.1.24-1.amd64"
date: 2020-07-30
forum: Ubuntu Development Version
---

### Post by dbergst on 2020-07-30
Error message is as follows:

Fatal error: Error while installing package: trying to overwrite '/usr/lib/lsp-plugins/lsp-plugins-r3d-glx.so', which is also in package lsp-plugins-common 1.1.22-0ubuntu1

---

### Post by mc4man on 2020-08-05
[https://bugs.launchpad.net/ubuntu/+source/lsp-plugins/+bug/1888684](https://bugs.launchpad.net/ubuntu/+source/lsp-plugins/+bug/1888684)

Just remove the  lsp-plugins-common package and then install whatever plugins you wish.

---

### Post by dbergst on 2020-08-07
> **mc4man said:**
> [https://bugs.launchpad.net/ubuntu/+source/lsp-plugins/+bug/1888684](https://bugs.launchpad.net/ubuntu/+source/lsp-plugins/+bug/1888684)

Just remove the  lsp-plugins-common package and then install whatever plugins you wish.

Thanks, mc4man.  Your suggestion and bug report were very helpful.

---

