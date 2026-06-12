---
title: "Getting a list of downloaded packages"
date: 2008-08-13
forum: Repositories &amp; Backports
---

### Post by Pyro.699 on 2008-08-13
Hello,

[LEFT]Is it possible to get a list of packages that you have downloaded and installed already? Use: I make the list, and reformat my computer, then import that list so that i dont have to search through all the packages again.

Thanks
~Cody Woolaver
[/LEFT]

---

### Post by null byte on 2008-08-13
```
dpkg -l | awk '{print $2}' > packages.txt
```

---

### Post by Pyro.699 on 2008-08-13
Thanks,

How would i go about importing that list?

---

