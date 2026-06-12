---
title: "Refresh LUN Mount's File Index"
date: 2012-09-21
forum: Server Platforms
---

### Post by genericusers on 2012-09-21
Forgive my terminology as I am a big beginner on Ubuntu
 
Scenario:
a Windows server has a NTFS LUN mount to a storage array with read/write rights. An Ubuntu server has the same LUN mount except with strictly read rights.
 
The problem:
When the Windows server writes a file to the LUN, that new file can be instantly seen in the LUN folder within Windows. The Ubuntu server does not see this new file since it has no need to refresh the LUN's file's index. Ubuntu appears to only update the file index when it either writes to the LUN (which will not be enabled) or if the LUN is dismounted and remounted.
 
How:
Can I force the Ubuntu server to update the file index without having to dismount the LUN first or write to it.
 
Thanks.

---

### Post by genericusers on 2012-10-01
Any ideas on the feasibility?

---

### Post by hasan.akgoz on 2012-10-02
You should use something made for this, like NFS , CIFS , SMB or NAS etc..

---

