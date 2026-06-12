---
title: "Special user config in any FTP - Server"
date: 2011-11-02
forum: Server Platforms
---

### Post by kurnosem on 2011-11-02
I need a special configuration for a group of users in a FTP-Server, I already did it very easily in Windows XP with Filezilla server, but I really cannot do it with pureftpd or vsftpd.

1º) I need a group of Virtual FTP users. (Not real unix users)
2º) Each user with his own user and password.
3º) Each time any user enters into the FTP server they must enter in a main directory.
4º) The may could read any file or subdirectory but they can only write in their own subdirectory.

Example:
3 users: user1, user2 and user 3

A directory with three directories:

/-              (all users can read, but not write)
 |---directory1 (user1 has all permissions)(all users can read, but not write)
 |---directory2 (user2 has all permissions)(all users can read, but not write)
 |---directory3 (user3 has all permissions)(all users can read, but not write)

And a "root" or "admin" user that has permissions everywhere...

with filezilla server and the config of user and permissions is really easy... but I have been searching for solutions in different ftp servers for ubuntu, and all are very difficult to config.

Thank you very much

---

### Post by kurnosem on 2011-11-03
anyone...???

---

