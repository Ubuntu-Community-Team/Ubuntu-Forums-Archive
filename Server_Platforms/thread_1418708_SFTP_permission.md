---
title: "SFTP permission"
date: 2010-02-28
forum: Server Platforms
---

### Post by saturngod on 2010-02-28
I'm using Ubuntu 9.10 in Amazon EC2.It's already install openssh-server.

I create a user but user can't access SFTP. How to give permission to access SFTP ?

I can't access also ssh. Error is

```
Permission denied (publickey).
```

How to config it ?

Thank

---

### Post by stlsaint on 2010-03-01
This means that you are trying to connect via password when the sshd_config on the server is setup to use key authentication, hence the error (publickey). 

At least thats what it means whenever i get that error on server...in a cloud i wouldnt know what your ssh setup was so i cant speak for it.

---

