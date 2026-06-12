---
title: "List of installed packages"
date: 2006-03-13
forum: Server Platforms
---

### Post by megadyptes on 2006-03-13
Folks!

Is there a way to list the names of installed packages on a server install, and possible filter them by keyword similar to the way apt-cache can be used to look for packages in the repositories?

Ta muchly

---

### Post by Koybe on 2006-03-13
Try this :
```
dpkg --get-selections
```
then you can filter with grep.
```
dpkg --get-selections | grep -i keyword
```

---

### Post by megadyptes on 2006-03-13
Perfect!

---

