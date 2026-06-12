---
title: "Samba 3.0.28a - ACL working 3.5.2 ACL not working"
date: 2010-04-23
forum: Server Platforms
---

### Post by Fooshnik on 2010-04-23
I upgraded Samba to 3.5.2 to enable Windows 7 to log in to the PDC. ACL was working with the Samba 3.0.28a that came with 8.04LTS. After upgrade I can now log in to the domain with Win 7 but ACL permissions are not working on Win7, XP or anything. They still show on the server but any attempt to change permissions on the workstation fails with "Access is Denied" and only user/group/other permissions are doing anything. Anyone know what changes for the ACL were made between the two versions? I know they're working on switching to VFS modules but setting "vfs objects = acl_xattr" did not help.

---

### Post by Fooshnik on 2010-04-24
No bites. Does anyone have ACL working with Samba 3.4.3 or newer?

---

