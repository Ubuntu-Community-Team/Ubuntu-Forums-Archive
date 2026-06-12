---
title: "Get rid of directory tree?"
date: 2006-08-29
forum: Server Platforms
---

### Post by geminias on 2006-08-29
Hi again, I'm getting a directory tree of the directories inside /var/www/ even though i set the document root of my new website to /var/www/newsite.  

I set the symbolic link correctly as well.  I'm guessing there is something i gotta change in the apache2.conf?

---

### Post by mssever on 2006-08-29
In apache2.conf, set DocumentRoot to wherever your document root should be. Then restart apache:
```
sudo apache2ctl graceful
```

---

