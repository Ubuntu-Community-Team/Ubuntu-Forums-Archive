---
title: "DEB -- Ubuntu version override"
date: 2007-09-29
forum: Repositories &amp; Backports
---

### Post by Sockerdrickan on 2007-09-29
Hi I have a DEB made for 7.04 but I use 7.10, how can I override this DEB's requirements?

---

### Post by Seisen on 2007-09-30
When you install the package try adding either -f or -force in the command.

```
sudo dpkg -f packagename
```

---

