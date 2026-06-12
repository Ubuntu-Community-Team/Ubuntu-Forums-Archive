---
title: "apache generates 403's"
date: 2007-02-18
forum: Server Platforms
---

### Post by jrobinson5 on 2007-02-18
So I installed apache2 on a Hoary server install (ie command line only) and copied a file, index.html, to /var/www. Problem is that whenever I try to access it I get a 403 forbidden. However I can still view the contents of the apache2-default folder just fine. Any ideas?

James

---

### Post by jtc on 2007-02-18
The problem is most likely that Apache simply don't have the permissions to read the file in question. This is easiest solved by making it globally readable.

```
chmod 644 index.html
```

(owner: read and write, group: read, others: read)

---

### Post by jrobinson5 on 2007-02-18
Wow, that was easy. I thought I had chmod'd it 777 but apparently I had not. (plus the fact that chmodding it 777 would have been really stupid.)

James

---

### Post by jrobinson5 on 2007-02-18
Figured it out: I was using chown instead of chmod. Would using chown instead of chmod damage anything?

---

### Post by jtc on 2007-02-18
The worst thing which could happen would be you getting some weird fileownerships. Nothing which can't easily be corrected.

---

