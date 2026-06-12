---
title: "suspicious ssh logs"
date: 2008-01-02
forum: Server Platforms
---

### Post by maerlma on 2008-01-02
I came back after the holiday and found some weird looking logs in my auth.log.

Jan  2 08:12:28 pariah sshd[22639]: subsystem request for sftp
Jan  2 08:12:40 pariah sshd[22639]: pam_env(ssh:setcred): No such user!?
Jan  2 08:12:40 pariah sshd[22639]: pam_env(ssh:setcred): No such user!?


Has anybody seen this before and should I be worried?

---

### Post by FreakTech on 2008-01-02
It looks like someone tried to create a secure ftp link to your system but was denied because the user name pariah was not in your user database, but I am not real familiar with ssh and sftp so I could be wrong.

---

### Post by kidders on 2008-01-02
FreakTech is right. Imo, there is no reason for concern, unless of course you weren't aware your SSH server is publicly accessible.

---

