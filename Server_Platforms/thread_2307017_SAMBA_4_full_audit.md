---
title: "SAMBA 4 full audit?"
date: 2015-12-21
forum: Server Platforms
---

### Post by edi3 on 2015-12-21
Hello,

are there any file/user activity logging function in Samba 4 like full_audit in older versions?

I'm using Ubuntu Server 14.04 and Samba 4

Best regards,
Edi

---

### Post by bab1 on 2015-12-21
> **edi3 said:**
> Hello,

are there any file/user activity logging function in Samba 4 like full_audit in older versions?

I'm using Ubuntu Server 14.04 and Samba 4

Best regards,
Edi
Yes there is a VFS module available.  See the man page```
man 8 vfs_audit
```

---

### Post by edi3 on 2015-12-22
Thank You for fast replay,

vfs_audit gives a lot of information about what is happening with file but not who (what samba user) is doing that.

Is there any module in Samba 4 that allows that?

---

