---
title: "file upload in php check"
date: 2012-02-03
forum: Server Platforms
---

### Post by subhojit on 2012-02-03
hello, i have done the file upload in php, and i want to know that is there any way to check that $_FILES["file"] is empty or not. the user may not want to upload any file, so how can I check that? help please

---

### Post by SeijiSensei on 2012-02-03
How about 

```
if (empty($_FILES['file'])) { stuff; }
```

---

