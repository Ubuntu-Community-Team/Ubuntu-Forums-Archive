---
title: "NTFS Permissions"
date: 2008-01-19
forum: Server Platforms
---

### Post by Deathmoon on 2008-01-19
I'm posting this here as it's a security concern and I can't seem to find an answer for it on the net or forums.  

The issue is that I have 7.10 (Desktop) running on a workstation that is shared by 2 users.  One user has limited access rights and the other user is essentially an administrator (I know that this is bad practice).  

I have a 2nd hard drive in the box that is a NTFS drive.  Currently, both users can access the drive and delete files.  I would like for it to only allow the admin this privilege.  How can I remove the drive from showing for the non-admin user or removing this access right?

Thanks in advance.

---

### Post by fuseblower1123 on 2008-01-19
right clicking on the drive and selection properties>permissions will allow you to change the access rights for various users and change them. if that doesn't work you can use chmod.

---

