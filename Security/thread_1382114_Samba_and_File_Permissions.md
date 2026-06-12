---
title: "Samba and File Permissions"
date: 2010-01-15
forum: Security
---

### Post by shadsnz on 2010-01-15
I've just installed Ubuntu 9.10 and Samba 3.4. I've shared a folder and have accessed the share from a Windows 7 client. However, I've struggled to configure the share and folder so that the Win7 client can create files and/or folders in the share. Kept getting Permission Denied errors. Finally, (using Webmin) I set the permissions on the file folder so that "Other" had write access. I don't understand why this was necessary (and how unsecure this is). I already had the write access checkbox ticked for "User" but it wasn't enough.

---

### Post by CharlesA on 2010-01-15
Are the file permissions on the folder set correctly? Does the person trying to create folders/files part of the owner or group on that folder?

If they aren't the owner or in the group, they would fall into the "other" category. If you add that user to the group that had write access to that folder, you should be fine.

---

