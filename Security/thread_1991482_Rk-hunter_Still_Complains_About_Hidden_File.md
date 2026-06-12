---
title: "Rk-hunter Still Complains About Hidden File"
date: 2012-05-30
forum: Security
---

### Post by user2037 on 2012-05-30
Adding these lines to /etc/rkhunter.conf does not help:
ALLOWHIDDENDIR="/dev/.initramfs"
ALLOWHIDDENDIR="/run/initramfs"

Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'

Anyone know of a solution?

---

### Post by CharlesA on 2012-05-30
Ignore it as a false positive.

---

### Post by user2037 on 2012-06-27
Ignoring is easier said than done. It also reduces the usefulness of the tool.

---

### Post by CharlesA on 2012-06-27
> **user2037 said:**
> Ignoring is easier said than done. It also reduces the usefulness of the tool.
The usefulness of a tool is determined by knowing how to properly use it. That includes knowing of any false positives it may report.

---

### Post by unspawn on 2012-06-27
> **user2037 said:**
> Anyone know of a solution?
Issue was fixed in CVS by revision 1.406 on Oct 20th 2011. Use white-listing but with RKH >= 1.4.0, released May 1st 2012.

---

