---
title: "Where is the PHP file saved?"
date: 2008-12-08
forum: Security
---

### Post by chunchengch on 2008-12-08
I run command 'sudo chkrootkit', and find some suspect PHP files, I would like to remove those, but I don't know where are these PHP files located? thanks for giving information.

---

### Post by Sarmacid on 2008-12-09
Try with the find command

```
find / -name "filename.php"
```

---

