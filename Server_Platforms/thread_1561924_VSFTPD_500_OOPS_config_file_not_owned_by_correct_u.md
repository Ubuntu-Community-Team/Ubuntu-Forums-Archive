---
title: "VSFTPD 500 OOPS: config file not owned by correct user, or not a file"
date: 2010-08-26
forum: Server Platforms
---

### Post by soul500l on 2010-08-26
I'm trying to install vsftpd on my computer. But in some way, it gives me this error: 

> 500 oops config file not owned by correct user or not a file.

**What I did:**
[LIST=1]
[*]I tried to change the users back from root to $user and this is the error when I try to type "vsftpd" on the terminal:
[LIST]
[*]"sudo chown root:$user vsftpd.conf" Error: config file not owned by correct user, or not a file.
[/LIST]
[LIST]
[*]"sudo chown $user:$user vsftpd.conf" Error: Must be started as root (see run_as_launching_user option)
[/LIST]
[/LIST]

I don't really know what type of user and group to change it to. Any help from you guys is appreciated.

---

### Post by K.Mandla on 2010-08-27
Moved to Server Platforms.

---

### Post by craigp84 on 2010-08-27
```
sudo dpkg-reconfigure vsftpd
```

---

