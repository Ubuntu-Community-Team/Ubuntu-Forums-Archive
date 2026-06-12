---
title: "uninstalling"
date: 2007-02-21
forum: Ubuntu System Panel
---

### Post by kelbizzle on 2007-02-21
How would one go about removing usp?

---

### Post by chanders on 2007-02-21
USP creates a .usp folder in your home directory so you need to remove that. Also you need to remove

/usr/bin/usp
/usr/bin/uspconfig

and

/usr/share/usp
/usr/lib/python2.4/site-packages/usp

Thats it!

---

### Post by PsyberOneZero on 2007-02-21
The newest version of the script now can uninstall usp as of rev. 146.
so just type ```
./usp_update uninstall
```

---

