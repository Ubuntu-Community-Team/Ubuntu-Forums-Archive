---
title: "Server password incorrect?"
date: 2008-10-15
forum: Server Platforms
---

### Post by Gannon8 on 2008-10-15
Hi. I installed Ubuntu Server Edition AMD64 with MySQL. At the prompt, I put my password in, and repeat it. The instillation accepts it and installs the server, but when I try to connect to the mysql database, I get an error saying I have the wrong password, but I know I am entering it in correctly. Is there any way to recover/reset the password?

My password has a '\' in it. Would that be the problem?

---

### Post by cariboo on 2008-10-15
As far as I know a "\" is the same as a space in Linux. The quick way to set a new password for mysql is:

```
dpkg-reconfigure mysql-server-5.0
```

You can reset the password in the dialogue box that pops up.

Jim

---

