---
title: "SFTP setup"
date: 2014-05-30
forum: Server Platforms
---

### Post by thuizt on 2014-05-30
Hello Experts,

We have a SFTP server with chrooted access for users from the (DMZ) outside
On the LAN inside we have Samba access to the same locations.
Internal users can provide the data that the external users can up/download.

The problem we encounter is that the file security is not maintained when files are put on the server through sftp or samba.
I'm also not sure that the users/groups setup we have is correct.

the file security on the files in the SFTP server is:

sftp_user:samba_group.

Any thoughts / help appreciated.

---

### Post by slickymaster on 2014-05-30
Moved to the **Server Platforms** sub-forum.

---

