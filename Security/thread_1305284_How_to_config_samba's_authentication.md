---
title: "How to config samba's authentication?"
date: 2009-10-29
forum: Security
---

### Post by tandkzy on 2009-10-29
My samba server use default config file. When I want to access from a XP machine, the system ask me to input username and passwd.
So I try to use smbpasswd program to add user, but it doesn't work.
Same article pointed out that ubuntu use testpam to do the authenticate work for samba, so I want to know how to set this thing.

---

### Post by cariboo on 2009-10-30
Just type the username and password of an account on the server. You have to set a username and password using the following commands:

```
sudo smbpasswd -L -a <username>
```

and it has to be enabled

```
sudo smbpasswd -L -e <username>
```

---

