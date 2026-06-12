---
title: "vsftpd &quot;secure_chroot_dir&quot;"
date: 2008-05-04
forum: Server Platforms
---

### Post by sprucio on 2008-05-04
Can anyone explain to me what the directive "secure_chroot_dir" is for? It seems like once you set chroot, the user is restricted to the users' home directory.

---

### Post by Webdemic on 2008-05-06
The default value for "secure_chroot_dir" (/usr/share/empty) should be sufficient (at least, I've never had to change it). This directive is different than "chroot_local_user", which is the directive that locks users in their home directory. "secure_chroot_dir" is used to lock the daemon in an unwritable folder when it is doing things that don't require filesystem access (at least, that's what I gather from the manpage):

> secure_chroot_dir: This option should be the name of a directory which is empty. Also, the directory should not be writable by the ftp user. This directory is used as a secure chroot() jail at times vsftpd does not require filesystem access.

Take care.

---

