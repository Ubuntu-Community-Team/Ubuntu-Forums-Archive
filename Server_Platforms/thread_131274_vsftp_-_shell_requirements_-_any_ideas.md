---
title: "vsftp - shell requirements - any ideas?"
date: 2006-02-16
forum: Server Platforms
---

### Post by jimwillsher on 2006-02-16
Hi,

I have a number of users which I want to give FTP access (read/write). They are valid users. However I don't want to give them shell access.

If I set their shell to /bin/false, they cannot login via ftp. As soon as I change their shell to /bin/bash they can login via ftp successfully.

I've looked at the check_shell parameter in vsftpd.conf but setting it to NO seemed to make no difference.

Any thoughts? (And please don't suggest changing to ProFTPD :???: )

Many thanks!


Jim

---

### Post by jimwillsher on 2006-02-16
I forgot to say. I found this thread here:

[http://ubuntuforums.org/showthread.php?t=44087](http://ubuntuforums.org/showthread.php?t=44087)

but setting to /bin/true also doesn't seem to work.

I'm running Breezy.


Jim

---

