---
title: "encrypt swap"
date: 2010-03-13
forum: Security
---

### Post by ipwnu on 2010-03-13
Is there a way to encrypt your swap partition after installation?

---

### Post by Agent ME on 2010-03-14
```
sudo ecryptfs-setup-swap
```
You might need the ecryptfs-utils package.

---

### Post by mkvnmtr on 2010-03-14
You can also use one of the apps in the secure-delete package to wipe your swap partition.

---

### Post by HermanAB on 2010-03-14
First read:
man swapon

---

