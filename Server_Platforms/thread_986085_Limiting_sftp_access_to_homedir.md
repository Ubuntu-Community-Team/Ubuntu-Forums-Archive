---
title: "Limiting sftp access to homedir"
date: 2008-11-18
forum: Server Platforms
---

### Post by paiwacket on 2008-11-18
ubuntu 8.04

How can I limit sftp access to the user's homedir, esp. for members of <users>?

Thanks,  -Barry

---

### Post by hictio on 2008-11-18
Yoou'll have to chroot the SSH daemon, you can do that with rssh, you'll have to install it, and configure it.
Take a look at this [SFTP For Business Use](http://freshmeat.net/articles/view/1576/) for hints.

---

