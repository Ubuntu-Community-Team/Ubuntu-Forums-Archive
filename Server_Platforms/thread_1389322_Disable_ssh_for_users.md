---
title: "Disable ssh for users"
date: 2010-01-24
forum: Server Platforms
---

### Post by Kemon on 2010-01-24
I have created my own server with php, mysql and pma.

I want to creat users and disable ssh so they can only user their username and password to get access to /home/<username> with a ftp program.

Or can I do it in an other way?

---

### Post by Roger_Smith on 2010-01-24
Taken from post: 
[http://ubuntuforums.org/showthread.php?t=292057]("http://ubuntuforums.org/showthread.php?t=292057")

> Edit /etc/ssh/sshd_config:
Code:

```
AllowGroups sshers
```

Now create the group sshers and add only the users that you want to allow to ssh into your box.

---

