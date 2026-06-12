---
title: "Access Control Lists"
date: 2007-10-25
forum: Server Platforms
---

### Post by InGunsWeTrust on 2007-10-25
Is there any way to make sure a file system can't mount unless it is mounted with access control list support? The security hole I am trying to close is one where you reboot using a live CD in order to just ignore all file permissions defined on the system. I know if a create an access control list I can limit access by user name but that doesn't help if somebody can just mount it without the acl option to bypass it.

---

### Post by /etc/init.d/ on 2007-10-25
No permissions will work if someone is able to reboot into a live CD.  If your data is not encrypted then somebody can access it, even if they need to take the HDD out of the case.

---

