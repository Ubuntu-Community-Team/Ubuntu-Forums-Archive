---
title: "Is bzip2 now obsolete in artful?"
date: 2017-05-02
forum: Ubuntu Development Version
---

### Post by harry332 on 2017-05-02
The compression tool bzip2 is, I think, considered obsolete in Ubuntu (Debian?).
For example, see this bug report (1687534):
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687534](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687534)

However, the newest file-roller (from 29. april) still depends on bzip2.
Does anyone know more about this here?

---

### Post by jbicha on 2017-05-02
.deb files are compressed with xz now (which caused a build problem for Ubuntu's Linux kernel that had opted in to bzip2 compression years ago because it was better than gzip). This has nothing to do with whether bzip2 or gzip is supported for other purposes.

---

