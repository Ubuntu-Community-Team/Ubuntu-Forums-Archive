---
title: "[SOLVED] samba join domain as non-root"
date: 2008-06-09
forum: Server Platforms
---

### Post by cdenley on 2008-06-09
I'm trying to set up a samba PDC using LDAP. I just got stuck trying to join the domain. I think it's related to samba not allowing non-root users to join the domain (create machine accounts) by default. I changed this on the server currently being used, but don't remember how.

---

### Post by cdenley on 2008-06-10
I believe this is the command I was looking for.
```

sudo net rpc rights grant admins SeMachineAccountPrivilege

```
It's still not working, but I think I'm one step closer.

---

