---
title: "apache and directory permissions"
date: 2007-09-11
forum: Server Platforms
---

### Post by poseid()n on 2007-09-11
Hi, ok so all my web files go in /var/www where the owner and group is root. As i don't wan't to be root to upload/change files, i created a new group, added users to that group and changed the owner on /var/www to be the new group with RWX. Would this pose any security risk?

---

### Post by kidders on 2007-09-12
Hi there & welcome,

> **poseid()n said:**
> Would this pose any security risk?Only in the sense that more people might now be permitted to alter your www files, without having access to sudo ... which may well amount to a security *improvement*, I suppose.

---

