---
title: "packagekit and python-aptdaemon.pkcompat"
date: 2012-02-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2012-02-23
```
The following packages will be REMOVED:
  packagekit
The following NEW packages will be installed:
  checkbox-qt python-aptdaemon.pkcompat whoopsie
The following packages will be upgraded:
  ubuntu-desktop
1 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.

```
Remove packagekit? I've serached through changelogs and could not find a sound answer...

---

### Post by dino99 on 2012-02-23
> **zika said:**
> ```
The following packages will be REMOVED:
  packagekit
The following NEW packages will be installed:
  checkbox-qt python-aptdaemon.pkcompat whoopsie
The following packages will be upgraded:
  ubuntu-desktop
1 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.

```
Remove packagekit? I've serached through changelogs and could not find a sound answer...

ubuntu use apparmor, packagekit is now removed

---

### Post by zika on 2012-02-23
> **dino99 said:**
> ubuntu use apparmor, packagekit is now removedThank You.

---

### Post by cariboo on 2012-02-23
> **dino99 said:**
> ubuntu use apparmor, packagekit is now removed

Packagekit, is a package management utility, Apparmor is a security module for the kernel, they have nothing to do with each other.

---

### Post by zika on 2012-02-23
> **cariboo907 said:**
> Packagekit, is a package management utility, Apparmor is a security module for the kernel, they have nothing to do with each other.But, as I've gathered from some other places, in the meantime, packagekit is depreciated and python-aptdaemon.pkcompat is to be installed. Am I wrong?

---

### Post by cariboo on 2012-02-23
Yes, but they aren't related, except that they may share a dependency.

---

### Post by zika on 2012-02-23
> **cariboo907 said:**
> Yes, but they aren't related, except that they may share a dependency.Thank You.

---

