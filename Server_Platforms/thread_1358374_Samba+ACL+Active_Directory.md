---
title: "Samba+ACL+Active Directory"
date: 2009-12-18
forum: Server Platforms
---

### Post by raleighb on 2009-12-18
I inherited a Ubuntu Server 6.10 file server setup to authenticate to a Windows Active Directory.  For the most part it works "ok".  However now I need to grant read/write permissions to only specific people on certain folders.  The problem is that the Domain Users group always gets read access.  If I remove it it comes back.  I have an idea that this is being caused by the person being in the Domain Users group and is therefore cascading the permission flags some how.  Here is the scenerio and I bet its common but I have had no real luck tracking down the answer in the billions of various opinions on the internet.

SCENERIO:
- Company Share
 - Management Folder
  - PersonnelReviews Folder
   - Dept_1
   - Dept_2
   - Etc.


I need only the Executive Group to have full control to the entire Management Structure.  And only the manager of the Department to have Full control over his/her specific department folder under PersonnelReviews.  

All users and Groups are AD User/Groups.

I know that this is somehow possible but for the life of me cannot seem to make it work.

---

### Post by kadeous on 2009-12-18
I'm still rather new with ubuntu server but I've been using webmin to administer it. There are tons of options under samba that I haven't even browsed yet. Perhaps you can give it a try and see if that will help with what your looking to do.

---

