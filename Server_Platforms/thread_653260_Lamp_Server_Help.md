---
title: "Lamp Server Help"
date: 2007-12-29
forum: Server Platforms
---

### Post by 89vision on 2007-12-29
I set up a lamp server and put phpmyadmin on there.  I got everything working except for when I try to run any php files firefox asks me to save it to my computer rather than running it.  Does this have to do with chmod permissions? Can anybody give me some insight?  Thanks in advance

---

### Post by andol on 2007-12-29
Enabled mod_php?

Unless you are sure, you can always give ut the output of the following command:

```
ls  /etc/apache2/mods-enabled/
```

No, it doesn't sound like it has anything to do with file permissions.

---

