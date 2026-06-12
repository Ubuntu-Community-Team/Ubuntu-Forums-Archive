---
title: "XFS rescue"
date: 2009-11-10
forum: Server Platforms
---

### Post by MMoudry on 2009-11-10
Hi,
I have the following problem, my XFS partition was corrupted and I can't seems to get it right to rescue it. When I boot from the server CD into the 'rescue system' there is no 'xfs_check' and 'xfs_repair' tools. Does anybody know any CD image that contains those tools and from which I could boot?

Mipam Moudry

---

### Post by scorp123 on 2009-11-11
> **MMoudry said:**
> When I boot from the server CD into the 'rescue system' there is no 'xfs_check' and 'xfs_repair' tools. ```
sudo apt-get install xfsprogs xfsdump
```

And yes, this works on the Live CD as well. So you boot your Live CD, issue above command, and voila ... your live session will have those programs.

---

