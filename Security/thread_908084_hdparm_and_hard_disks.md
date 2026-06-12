---
title: "hdparm and hard disks"
date: 2008-09-02
forum: Security
---

### Post by sulekha on 2008-09-02
I have read in a book that although it is safe to view information about features of your hard disks (using hdparm), it can potentially damage your hard disk to change some of those settings

how valid is this claim ?

---

### Post by cdenley on 2008-09-02
If you look at the man page, you will see many warnings for certain options such as "DANGEROUS" or "Use with knowledge and extreme caution as this can easily hang or damage your system". So I would consider this claim valid, and I wouldn't use any command switch you don't fully understand.
```

man hdparm

```

---

