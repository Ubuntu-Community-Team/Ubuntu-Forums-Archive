---
title: "SFTP with Pre-Shared Keys"
date: 2010-11-22
forum: Server Platforms
---

### Post by divided on 2010-11-22
I understand how to set up an SFTP server and generate my own pre-shared keys.  The question is, how do I set up an SFTP server with pre-shared keys that have been provided to me?  Is it as simple as placing those files on the server where they are supposed to be?

Thanks in advance.

---

### Post by divided on 2010-11-23
Can anyone help?

---

### Post by cariboo on 2010-11-23
If you already have generated the keys and have them on the system you normally use, all you have to do is copy the keys to the server using:

```
ssh-copy-id user@server
```

the above command assumes you have the public key in ~/.ssh/id_rsa.pub

---

### Post by divided on 2010-12-08
I've fixed this problem.  Apparrently, all I had to do was install openssh-server and then put the keys provided to me in /%h/.ssh/authorized_keys, make sure that the user owned the directory and the file, and make sure that the file had the correct permissions.

---

