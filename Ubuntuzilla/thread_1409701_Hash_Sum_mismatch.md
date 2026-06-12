---
title: "Hash Sum mismatch ?"
date: 2010-02-17
forum: Ubuntuzilla
---

### Post by kansasnoob on 2010-02-17
Is this just a temporary thing?

```
Failed to fetch http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/main/binary-i386/Packages.gz  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by nanotube on 2010-02-17
> **kansasnoob said:**
> Is this just a temporary thing?

```
Failed to fetch http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/main/binary-i386/Packages.gz  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.
```

yes - takes some time for all the files uploaded to propagate to all mirrors... so if you happen to do an apt-get update shortly after a fresh upload, you'll get that. if you get it, just wait another few minutes, and try an apt-get update again, and problem should go away.

---

### Post by kansasnoob on 2010-02-18
I was pretty sure that was the case but thought it'd be good to give a shout :)

---

### Post by nanotube on 2010-02-18
> **kansasnoob said:**
> I was pretty sure that was the case but thought it'd be good to give a shout :)

never hurts :)

---

