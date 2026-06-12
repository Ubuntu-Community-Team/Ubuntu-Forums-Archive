---
title: "User Permissions?"
date: 2008-07-17
forum: Security
---

### Post by davidshq on 2008-07-17
I am having some trouble with my FTP account. I have two FTP users. The one is a member of the group users. The other is a member of the group users and a higher level group. The first user just updated some files on the FTP server and the permissions where changed to reflect their login as the user and the group as users. Now my second individual can no longer upload files over these existing files - they get a "permission denied" error int he FTP.
The second user was not previously in the users group, I just added them, but the error is still there. Do I need to somehow reload the permissions so the server sees that the higher level user is now in the group users?
David.

---

### Post by davidshq on 2008-07-17
Duhh...I fixed it. In my permissions I had the user able to read/write/etc. but not for group. I changed this and it began working. This raises a new question. How can I tell all my files in specific directories to give the Group read/write/list privileges while at the same time not blowing out current privileges for user/other?
David.

---

