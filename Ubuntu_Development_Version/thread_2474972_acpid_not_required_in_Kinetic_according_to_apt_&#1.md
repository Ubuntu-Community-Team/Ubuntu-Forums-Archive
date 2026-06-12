---
title: "acpid not required in Kinetic according to apt &#129300;"
date: 2022-05-12
forum: Ubuntu Development Version
---

### Post by Yahoé on 2022-05-12
Hi,  apt is reporting that acpi-support and acpid are not required on this Kinetic system and can be removed.  Any idea why?

---

### Post by Frogs Hair on 2022-05-13
There is a new version in the works or available.
 [https://launchpad.net/ubuntu/+source/acpid](https://launchpad.net/ubuntu/+source/acpid)

---

### Post by osse7 on 2022-05-16
acpi-support is required by each "flavor"-desktop package
and acpid is a dependency of the previous

---

### Post by Yahoé on 2022-05-18
Thank you @Frogs Hair and @osse7. As of today, apt is still reporting that acpi-support and acpid are not required on this Kinetic system and can be removed.  Surely an early development glitch that will get fix soon enough.

---

