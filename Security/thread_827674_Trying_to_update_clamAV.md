---
title: "Trying to update clamAV"
date: 2008-06-13
forum: Security
---

### Post by TheAJKMan on 2008-06-13
Hi there guys. Hoping you'll bear with this relative newb and give me some advice as to ho to update my virus defs in clamAV 3.04 I d/l and installed it using the pacakage manager in Ubuntu and wanted to update my defs. It said the following ...."You must be root to install updates." Errr, how do I now update my defs and keep them current.

Thanks in advance.
TheAJKMan

---

### Post by Oldsoldier2003 on 2008-06-13
> **TheAJKMan said:**
> Hi there guys. Hoping you'll bear with this relative newb and give me some advice as to ho to update my virus defs in clamAV 3.04 I d/l and installed it using the pacakage manager in Ubuntu and wanted to update my defs. It said the following ...."You must be root to install updates." Errr, how do I now update my defs and keep them current.

Thanks in advance.
TheAJKMan

Use sudo. If i recall correctly freshclam is the utility for updating ClamAV, so the command is

```
sudo freshclam
```

---

### Post by TheAJKMan on 2008-06-13
Thanks, that did the trick, better make a note of it for future reference. Me and my No3 colander memory ;)

---

### Post by hyper_ch on 2008-06-13
what do you need antivirus for anyway?

---

