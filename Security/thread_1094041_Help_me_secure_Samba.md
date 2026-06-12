---
title: "Help me secure Samba"
date: 2009-03-12
forum: Security
---

### Post by choco140 on 2009-03-12
Hi,

I would like to secure my Samba share as much as I can and reduce access to local machine only (192.168.1.x).

Can somebody tell me what I need to do in order to do that properly (firewall, smb.conf, etc...)?

My idea is to try and lock Samba access as much as I can still leaving local users the ability to connect.

Thanks.

---

### Post by Nepherte on 2009-03-12
Put this in your smb.conf file under [global]:
```
hosts allow = 192.168.1.0/24
hosts deny = 0.0.0.0/0
```

---

### Post by choco140 on 2009-03-12
Thanks.

Do you reckon that it would be safe enough?

Would you consider that I should also restrict the access through IPTables (not sure how to do that)?

---

### Post by Nepherte on 2009-03-12
It should be sufficient enough. There's no reason to do exactly the same on more than one place. When you try to change something, you will have to make the change twice, kinda stupid if you ask me. You might also forget about one place.

---

### Post by choco140 on 2009-03-13
Thanks.

---

