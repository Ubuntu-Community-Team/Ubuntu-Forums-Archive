---
title: "Setup a ftpd with multiuser shares?"
date: 2010-09-12
forum: Server Platforms
---

### Post by wconstantine on 2010-09-12
I want to share a directory (and all subdirs) via an FTP service to several users. I have searched around a bit and I think it's quite confusing to set this up. I want to have access to the files too, don't want to login as root to access the files.

Should I include my account in ftpgroup and chgrp on the directory for them to be able to read?

---

### Post by Bachstelze on 2010-09-12
Do you also want to chroot the accounts?

---

### Post by wconstantine on 2010-09-12
> **Bachstelze said:**
> Do you also want to chroot the accounts?

If that means that the users won't be able to go below in the shared directory, then definitely yes. That dir and every dir in it should be accessible by several users and me. But they shouldn't be able to go cd .. and access the parent directories.

---

### Post by inphektion on 2010-09-12
use vsftpd with virtual users.  you can set it up exactly as you want, they can be chrooted and better when not actual /etc/passwd accounts.

---

