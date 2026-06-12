---
title: "Ubuntu underlying-changes to users-admin tool"
date: 2010-05-04
forum: Security
---

### Post by MK++ on 2010-05-04
Hi,

I surely know users-admin is different in Ubuntu. The question is:

How does users-admin tool apply user restrictions/rights; ones like "Use Modems", "Mount FUSE filesystems", ...etc?

If I would like to do same tweaking to user accounts through command line and/or config files, where and how would I do that? Is it PAM-Limits? Is is a mix of security settings? Is is AppArmor?


Any help/guidance would be appreciated.

---

### Post by cdenley on 2010-05-04
I think it is all done with group memberships:

Mount FUSE filesystems = member of "fuse" group
Use Modems = member of "dialout"

---

