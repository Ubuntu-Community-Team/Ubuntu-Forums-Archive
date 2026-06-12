---
title: "Samba PDC and ACL's?"
date: 2008-05-23
forum: Server Platforms
---

### Post by jedimastermopar on 2008-05-23
I was wondering if anyone here is running a Ubuntu PDC with Samba and has ACL security working? ALl of the documentation I can find refer to there being a windows server running as the PDC.

---

### Post by freebeer on 2008-05-23
I'm running Samba as a PDC.  I'm just using basic authentication.  I'm unfamiliar with ACL.

---

### Post by jedimastermopar on 2008-05-23
ACL's as in Access Control Lists, lets you set permisions on the files and folders of shares with more fine grain detail. EG access to multiple users and groups versus just one group and one user  and Everyone.

---

### Post by freebeer on 2008-05-23
[This]("http://www.bluelightning.org/linux/samba_acl_howto/") article, while old, indicates that the kernel needs to be patched for ACL to work.  Being old, I don't know if it has been subsequently adopted in later kernels.

Just something that jumped out at me.

---

