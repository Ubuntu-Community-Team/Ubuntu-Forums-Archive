---
title: "ssh/sftp ignore file ownership in home directory"
date: 2008-10-26
forum: Server Platforms
---

### Post by johnR2 on 2008-10-26
sftp and ssh appear to ignore file ownership when logged in as an ordinary (non-admin) user in the user's home directory. Both allow the remote user to delete read-only files owned by root. Does anyone know of a way to enforce the file permissions?

---

### Post by Dr Small on 2008-10-26
If there is a file owned by root in "userB"s $HOME, he can delete the file.

---

### Post by johnR2 on 2008-10-26
Thanks. Believe it or not I'd never noticed that before. In the past I've tried rm -rf on a directory tree belonging to root and got `permission denied', and just assumed a user couldn't delete files owned by root. A file or an empty directory can be removed, but a directory tree with files in can't.

I'll use chattr +i on files that need to be non-removable.

---

