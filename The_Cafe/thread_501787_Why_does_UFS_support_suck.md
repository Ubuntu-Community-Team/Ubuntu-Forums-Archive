---
title: "Why does UFS support suck?"
date: 2007-07-15
forum: The Cafe
---

### Post by Iandefor on 2007-07-15
Why is it that UFS support is so lacking in the Linux kernel? I've been playing around with FreeBSD and writing between the UFS partition FreeBSD is on and my ext3 partition is a nightmare.

The Linux kernel doesn't have working UFS write support and the ext3 support in the FreeBSD kernel is even worse. The documentation for the ext module warns that reading from an ext partition might lead to a kernel panic.

Does anybody know why this kind of basic support would be so wonky?

---

### Post by prizrak on 2007-07-15
Not sure about UFS but since EXT is a 100% open/free FS format I suspect it has more to do with developers and how they choose to handle it rather than actual technical issues.

---

