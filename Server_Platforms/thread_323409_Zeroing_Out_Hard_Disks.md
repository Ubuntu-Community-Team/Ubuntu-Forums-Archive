---
title: "Zeroing Out Hard Disks"
date: 2006-12-22
forum: Server Platforms
---

### Post by JPMaximilian on 2006-12-22
What application is there for zeroing out/writing random data to hard disks?

---

### Post by po0f on 2006-12-22
JPMaximilian,

```
[FONT="Courier New"]$ dd if=/dev/zero of=/dev/hda[/FONT]
```

[EDIT]

Of course, replace /dev/hda with whatever hardrive you want wiped.  ;)

---

### Post by jexxie on 2006-12-22
If you're looking for a 'secure' method of cleaning hard drives, try DBAN.

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

