---
title: "Samba Security Per Share?"
date: 2008-07-15
forum: Security
---

### Post by warchief_ryan on 2008-07-15
I might already know the answer to this but, does anyone know if you can set samba security on a per share basis? I want to require users to have to enter a username and pass on one share but not the other... :)

---

### Post by cdenley on 2008-07-15
> **warchief_ryan said:**
> I might already know the answer to this but, does anyone know if you can set samba security on a per share basis? I want to require users to have to enter a username and pass on one share but not the other... :)

The security option in smb.conf can only be used globally. You can tell by the (G) next to it in the manpage.
```

man smb.conf

```
G = global
S = share

---

