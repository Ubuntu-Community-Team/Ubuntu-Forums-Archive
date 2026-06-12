---
title: "linux delete privileges"
date: 2007-03-09
forum: Server Platforms
---

### Post by Kbob87 on 2007-03-09
I'm deploying a system auditor across my network, and this auditor requires read/write/execute privileges to a smb share. I want the audit process to be completely transparent to the end user, therefore i set up a Linux samba server with share level security settings which require no credentials what so ever. All of this works just fine.

here is my share configuration.

[AUDIT]
        comment = AuditWizard Database
        path = /home/audit
        browseable = yes
        writable = yes
        create mask = 0777
        directory mask = 0777
        guest ok = yes
        force user = nobody
        force group = nogroup


My problem exist at the privilege level. When users log in to my network their login script runs the auditor executable that is in this share, then once the auditor finishes its scan, it uploads the data it collected into another folder on the same share. For obvious reasons, I do not want the end users to have the ability to delete this data. Is there any way to set up Linux permissions for a user/group to have read/write/execute privileges, but no delete privileges.

I have tried the sticky bit, but this method does not work due to the fact that the file is owned by the creator "nobody". 

Also I have also tried the ACL approach, but this only seems to makes the current Linux permissions more flexible, it does not expand the ability to make a file/folder non-deletable.

---

### Post by Mr. C. on 2007-03-10
As smbd is running as user "nobody", there is no way to distinguish one user from another.  Since  smdb will be writing the audit file, it can delete it too.

Instead of share-level security (il.e. none), use user-level security, which is a much better idea anyway. Share-level security is like Windows 95/98 - all or none.

MrC

---

