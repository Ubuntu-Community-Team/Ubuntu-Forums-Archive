---
title: "os-prober"
date: 2017-02-02
forum: Ubuntu Development Version
---

### Post by flocculant on 2017-02-02
Just ftr.

Bug with os-prober currently means if you have grub booting from zesty AND the machine has other installs on it - then using os-prober (eg with update-grub) will cause the other installs to disappear from the boot menu.

This also affects installing alongside - you'll find that the installer doesn't see any existing installs.

[lpbug]1660159[/lpbug]

If you mount the other installs and then run update-grub it should find them again.

---

