---
title: "HU sudo 1.9.5p2-2ubuntu1 upgrade"
date: 2021-02-15
forum: Ubuntu Development Version
---

### Post by zika on 2021-02-15
After upgrade of package sudo there was an error stating that sudo dows not have uuid 0 etc. Of course, that was because root was not owner of /usr/bin/sudo and /usr/lib/sudo/sudoers.so. Also, permissions were wrong. Fixable in several ways, for me the fastest was to boot in maintenance mode and correct what was wrong. So, do not despair, it is, even easily, fixable.

Resolution: 
```
sudo (1.9.5p2-2ubuntu3) hirsute; urgency=medium

  * No change rebuild with fixed ownership.

 -- Dimitri John Ledkov <xnox@ubuntu.com>  Thu, 18 Feb 2021 00:03:21 +0000
```

---

