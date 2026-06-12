---
title: "Recommendations for a file hosting server"
date: 2009-02-14
forum: Server Platforms
---

### Post by fommil on 2009-02-14
Dear all,

I would like to set up a secure file hosting server on an Ubuntu Hardy installation. However, the server should be able to be accessed from external Windows, Apple and Linux desktops. Security is critical... all communication should be over an SSL connection and authenticated in some sane (preferable easy to configure) way.

Any advice? I'd rather not have to set up login accounts on the server, preferring authentication by a database or file lookup.

---

### Post by hyper_ch on 2009-02-14
my suggestion would be to use ubuntu server, with openssh-server running MySecureShell on it and restricted system users.

they then can use [http://www.winscp.com](http://www.winscp.com) for windows. Filezilla can also use SCP/SFTP if I'm not mistaken... I'm sure there's something for mac also. On linux you can use Konqueror/Dolphin and also other tools.

But one question: Should users be able to share folder among each other? And are you also afraid of physical access?

---

### Post by fommil on 2009-02-14
Thanks! This was actually my first thought, but doesn't it require system users? I'd really prefer to have authentication to the files separate from the system users.

The files on the server should be considered completely shared among all users that have access. Perhaps a read-only option, but for now let's say all users have write access and no file "belongs" to anybody.

Physical access is not a concern. The server is a virtual machine and there are no system users other than the administrators.

> **hyper_ch said:**
> my suggestion would be to use ubuntu server, with openssh-server running MySecureShell on it and restricted system users.

they then can use [http://www.winscp.com](http://www.winscp.com) for windows. Filezilla can also use SCP/SFTP if I'm not mistaken... I'm sure there's something for mac also. On linux you can use Konqueror/Dolphin and also other tools.

But one question: Should users be able to share folder among each other? And are you also afraid of physical access?

---

### Post by hyper_ch on 2009-02-14
yeah, this approach required system users because you authenticate through ssh server. I don't really see what the problem with that is. :) as for sharing, that might be a problem. I use MySecureShell to disallow them shell access and to chroot them to their own home directory.

I haven't used anything else for a long time. Maybe proftpd would be besser. I think it supports a sftp mode only.

---

