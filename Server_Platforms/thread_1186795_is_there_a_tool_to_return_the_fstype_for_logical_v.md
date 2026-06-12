---
title: "is there a tool to return the fstype for logical volumes?"
date: 2009-06-13
forum: Server Platforms
---

### Post by Polaris96 on 2009-06-13
Does anybody know of a command line tool that can discover the fstype on a logical partition created in lvm2?

---

### Post by Cheesemill on 2009-06-14
If its mounted then a
```
df -kTh
```
should tell you filesystem type.

---

### Post by Polaris96 on 2009-06-15
Thank you, Cheesemill.  That worked very well.

---

