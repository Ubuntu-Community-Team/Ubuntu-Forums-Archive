---
title: "Enable ACL (Access Control List) on production server"
date: 2012-03-10
forum: Server Platforms
---

### Post by TeamScience on 2012-03-10
Hi

I have a Ubuntu 10.04.4 server that hosts a couple of sites and email (virtual). One of my clients wants to run Redmine and Git as a project site. One of the steps calls for ACL to be setup in fstab. As this is a live server I'm nervous to just do this as I only have SSH access. Google produces too many variations.

My fstab is:
```
proc /proc proc defaults 0 0
none /dev/pts devpts gid=5,mode=620 0 0
/dev/md0 none swap sw 0 0
/dev/md1 /boot ext3 defaults 0 0
/dev/md2 / ext3 defaults 0 0
```

Could somebody give some guidance in implementing ACL in the above settings?

Regards
Brenton

---

