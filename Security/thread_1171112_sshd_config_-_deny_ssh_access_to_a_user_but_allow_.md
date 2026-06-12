---
title: "sshd config - deny ssh access to a user but allow scp"
date: 2009-05-27
forum: Security
---

### Post by graysky on 2009-05-27
Anyone?  Can I deny ssh access to a particular user but allow said user to use scp?  Thus far I can only accomplish the deny part by adding the following line to my /etc/ssh/sshd_config
```
DenyUsers user1
```

Also, said user needs full local access and /bin/bash as the shell.  Thanks!

---

### Post by The Cog on 2009-05-27
This might be what you're looking for...
[http://mysecureshell.sourceforge.net/](http://mysecureshell.sourceforge.net/)

---

