---
title: "Ecryptfs: Recover the &quot;recovery password&quot;"
date: 2010-06-28
forum: Security
---

### Post by Finog on 2010-06-28
If your ecryptfs recovery password (that string of ASCII hex values you get when you first set ecryptfs up for your Private directory) has been destroyed, is there a way to get it back if you still have the mount password for ecryptfs?

Thanks!

---

### Post by Bachstelze on 2010-06-28
```
ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase
```

---

