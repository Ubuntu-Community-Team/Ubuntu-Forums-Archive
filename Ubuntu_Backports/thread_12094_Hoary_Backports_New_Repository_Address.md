---
title: "Hoary Backports: New Repository Address"
date: 2005-01-21
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-21
As you may have already read, Hoary backports will be Subversion (sorta CVS) driven, to allow multiple backporters, maximum uptime, and most efficient backporting. I plan to offer backports for **ALL** architectures that Ubuntu supports.

David Longo of Somnium Computing has allowed me to host the new Ubuntu Backports tree on his server. It'll be located at:
[http://cloud9.somniumcomputing.com:81/ubuntu/backports/](http://cloud9.somniumcomputing.com:81/ubuntu/backports/)

(Yes, the :81 is required -- he serves on a nonstandard port. APT handles it perfectly)

Example lines:
```

#stable backports
deb http://cloud9.homelinux.net:81/ubuntu/backports hoary-backports main restricted multiverse universe

#stable extras
deb http://cloud9.homelinux.net:81/ubuntu/backports hoary-extras main restricted universe multiverse

```

If you're beta-testing, add another pair of the above, only with "hoary-backports-staging" and "hoary-extras-staging". Again, this is for BETA TESTERS. We strive to mark packages stable within 7 days of backporting, so just hang tight!

---

