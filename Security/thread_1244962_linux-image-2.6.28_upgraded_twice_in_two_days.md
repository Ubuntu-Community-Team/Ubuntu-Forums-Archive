---
title: "linux-image-2.6.28 upgraded twice in two days"
date: 2009-08-20
forum: Security
---

### Post by g0nad on 2009-08-20
linux-image-2.6.28 upgraded twice in two days on my system

On the 18th:
  linux-image-generic 2.6.28.14.19 -> 2.6.28.15.20

On the 19th:
  linux-image-2.6.28-15-generic 2.6.28-15.48 -> 2.6.28-15.49

(relevant section of aptitude's log attached)

It's not often I see kernels being dropped out so quickly.

[I would have prefixed this to ubuntu_alternate but that's not there so I've just gone with 'ubuntu']

---

### Post by warreno on 2009-08-20
Yup, I got that too. Jaunty (9.04) is probably being patched here and there. If it bugs you a lot, set your update manager to check once a week instead of daily:

System -> Administration -> Update Manger

Click Settings.

---

### Post by Agent ME on 2009-08-21
When a kernel upgrade happens, you don't need to immediately reboot. It will just keep using the old kernel until you do, so frequent kernel updates shouldn't be an issue (unless you have a slow internet connection and updates hog it frequently).

---

### Post by MythAaron on 2009-08-21
I, for one, consider it a good upgrade.  My myth box plays HD video much better now.

---

