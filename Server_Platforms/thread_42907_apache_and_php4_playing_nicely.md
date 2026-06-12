---
title: "apache and php4 playing nicely"
date: 2005-06-19
forum: Server Platforms
---

### Post by KingBahamut on 2005-06-19
or commonly known as 

how to get the browser to stop trying to open php files and load them properly ? 

=)

---

### Post by LordHunter317 on 2005-06-19
Seeing how many times this has come up, please trying searching the forums first and see if you can't find the answer for yourself.

---

### Post by GrumpySimon on 2005-06-20
Add this line to the mime type section of your httpd.conf:
```

AddType application/x-httpd-php .php

```

& restart apache.

--Simon

---

