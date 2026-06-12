---
title: "vsftpd virtual users (PAM) permissions"
date: 2009-06-24
forum: Server Platforms
---

### Post by memor2000 on 2009-06-24
Hi everybody,

I have a question about users folders permissions usgin PAM authentication in vsftpd.

The system:

- Ubuntu 8.04/9.04 server edition
- vsftpd with PAM authentication (Apache) and configuration file for each users.

All works fine, but now I need to do, for example, this:

- a user named *user1*
- *user1*'s ftp home folder is *folder1*
- inside *folder1* there are other two folders: *folder2* and *folder3*. Inside *folder2* *user1* can read and write, inside *folder3* *user1* can only read.

Is this solution possible with PAM authentication (with Apache)?
If no, are there other way to do this with virtual users?

Thanks a lot

---

### Post by memor2000 on 2009-07-03
...anybody can help me, please? ](*,)

---

