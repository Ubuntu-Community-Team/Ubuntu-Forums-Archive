---
title: "Ubuntu server upgrade 11.10 to 12.04"
date: 2012-05-20
forum: Server Platforms
---

### Post by crashdogy on 2012-05-20
OK so was doing the upgrade every thing was going fine but when it started to ask if i want to keep default programs.  I some how mad it stop the upgrade.  so what do now can I just start over or is there a way to resume upgrade ?

---

### Post by CharlesA on 2012-05-20
You can try running:

```
sudo do-release-upgrade
```

Hopefully you made a backup before trying to upgrade it originally.

---

### Post by crashdogy on 2012-05-20
Said no new version ?

---

### Post by CharlesA on 2012-05-20
How did you do the upgrade originally?

---

### Post by upstatelabs on 2012-09-28
I have the same problem, except mine crashed during do-release-upgrade from 10.04LTS to 12.04 LTS.
I retried do-release-upgrade at the rescue prompt but got 'no new version found'.
I then tried dpkg --configure -a which at first seemed to be working, but then froze at the bind9 start.
I am at a loss, is a full reinstall my only option now?  I hate to lose my lvm and samba configurations, but I don't know what else to try.

---

### Post by d4m1r on 2012-09-28
> **upstatelabs said:**
> is a full reinstall my only option now?

Unfortunately, pretty much yes.

---

