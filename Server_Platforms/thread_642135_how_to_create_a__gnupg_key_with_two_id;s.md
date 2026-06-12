---
title: "how to create a  gnupg key with two id;s"
date: 2007-12-16
forum: Server Platforms
---

### Post by lex1 on 2007-12-16
how to create a gunpg key with two ids (two ids on the same key)


ie

the key has the id

[email]send@mydomain.com[/email]
and
[email]config@mydomian.com[/email]


thanks

lex1

---

### Post by gaten on 2007-12-19
use the **--edit-key** option. More about it in the gpg man page, but for starters:
```
gpg --edit-key key
adduid
```

---

