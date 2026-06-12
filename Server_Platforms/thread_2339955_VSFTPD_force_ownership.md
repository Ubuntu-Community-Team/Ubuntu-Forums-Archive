---
title: "VSFTPD force ownership"
date: 2016-10-14
forum: Server Platforms
---

### Post by dgfrench on 2016-10-14
I have setup VSFTPD on Ubuntu 16.04 Desktop and created a list of users but when they create directories or upload files they cannot be accessed by other users. What is the best practice to allow all users to view others' files/directories but keep up with who created/uploaded what & when, etc.?

---

### Post by bab1 on 2016-10-14
> **dgfrench said:**
> I have setup VSFTPD on Ubuntu 16.04 Desktop and created a list of users but when they create directories or upload files they cannot be accessed by other users. What is the best practice to allow all users to view others' files/directories but keep up with who created/uploaded what & when, etc.?
All users in a common user group and the user group and SGID bit set on the root of the vsftp shared directory.

---

