---
title: "winSCP error..."
date: 2008-04-02
forum: Server Platforms
---

### Post by insineratehymn on 2008-04-02
Hi, alot of questions today, huh? ;)

Make sure that the server is running OpenSSH.

---

### Post by MJN on 2008-04-03
...and that an SFTP sub-system is enabled with **subsystem sftp /usr/lib/openssh/sftp-server **in **/etc/ssh/sshd_config**.

Mathew

---

