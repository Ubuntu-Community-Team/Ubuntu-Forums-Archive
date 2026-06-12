---
title: "Questions on local host."
date: 2006-09-16
forum: Server Platforms
---

### Post by Ob1 on 2006-09-16
just scanned 127.0.0.1

```
PORT      STATE SERVICE
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
631/tcp   open  ipp
40759/tcp open  unknown
51314/tcp open  unknown
Device type: general purpose
Running: Linux 2.4.X
OS details: Linux 2.4.7 (x86)
```

"netbios-ssn" and "microsoft-ds" might this be realted to my XP partition?

And how do i close these ports?

---

### Post by skymt on 2006-09-18
Those ports are used by Samba. If you don't need it, uninstall it.

---

