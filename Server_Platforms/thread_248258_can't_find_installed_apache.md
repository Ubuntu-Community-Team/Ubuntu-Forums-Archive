---
title: "can't find installed apache"
date: 2006-08-31
forum: Server Platforms
---

### Post by rawoo on 2006-08-31
Newbie question here.

I d/l the apache2 source code and had to modify one of the parameters in the spec file according to instructions given by and for virtualmin to work correctly. Then using ./configure, make and sudo make install, everything appears to work fine. But I am unable to locate the executable file. Any ideas?

---

### Post by chrisfay on 2006-08-31
Terminal:

```
whereis apache2
```

I think its /usr/sbin/apache2

---

