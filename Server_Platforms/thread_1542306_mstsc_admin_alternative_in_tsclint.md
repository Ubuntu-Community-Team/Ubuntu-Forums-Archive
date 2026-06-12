---
title: "mstsc /admin alternative in tsclint?"
date: 2010-07-30
forum: Server Platforms
---

### Post by SlugSlug on 2010-07-30
On windows I use 'start > run > mstsc /admin' 
to get the Administrator with ID0  on win terminal servers

How can I achieve the same login from ubuntu?

---

### Post by SlugSlug on 2010-08-02
bump

---

### Post by lykwydchykyn on 2010-08-02
try:
```

rdesktop -0 hostname

```

that's a dash followed by a zero (not capital O)

---

### Post by SlugSlug on 2010-08-02
cheers, I'll try tomorrow

---

### Post by bronkeydain on 2011-02-10
> rdesktop -0 hostname

Worked for me thanks

---

### Post by SlugSlug on 2011-02-10
aye and me thanks, - sorry I forgot to post back

---

### Post by Musrum on 2011-08-07
Using tsclient, change you rdp file to:

```
attach to console:i:1
```

---

