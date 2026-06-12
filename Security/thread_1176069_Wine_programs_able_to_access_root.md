---
title: "Wine programs able to access root?"
date: 2009-06-01
forum: Security
---

### Post by bitf on 2009-06-01
A Friend gave me an old (Still sealed) copy of Star Office 5.1 (Just for fun). The Linux version wouldn't install, so I ran the Windows Version on WINE. When I tried to open a file, the file I was presented with folders I'm usually only able to access in root. While the program crashes before I can do anything, could this be exploited by malware, which could install a WINE program that would allow the malware to access and edit key config and registry files or worse?

---

### Post by cdenley on 2009-06-02
By default, wine maps your root filesystem. It's not exactly the most secure default setting. You can change drive settings by running this command
```

winecfg

```

---

### Post by bodhi.zazen on 2009-06-02
I agree. See the wine section in the security sticky at the top of these forums.

On the flip side of the coin, wine is an application like any other and while you can browse to you / you can not make modifications, unless you are running wine as root, which is a violation of the first rule of wine ...

never run wine as root.

---

