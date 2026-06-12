---
title: "Lunar: keepassxc and firefox snap"
date: 2023-01-19
forum: Ubuntu Development Version
---

### Post by MyMurry on 2023-01-19
Hello,

my firefox doesn't find my keepassxc. How can I find the problem? Must I use keepassxc as snap or the normal version?

Regards

---

### Post by MyMurry on 2023-01-19
I got it running:

flatpak permission-set webextensions org.keepassxc.keepassxc_browser snap.firefox yes

What does this do?

---

### Post by MyMurry on 2023-01-19
The same result can be achieved with the following DBus call:
 qdbus org.freedesktop.impl.portal.PermissionStore /org/freedesktop/impl/portal/PermissionStore org.freedesktop.impl.portal.PermissionStore.SetPermission webextensions true org.keepassxc.keepassxc_browser snap.firefox yes

---

