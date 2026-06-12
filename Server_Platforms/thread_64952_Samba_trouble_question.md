---
title: "Samba trouble question"
date: 2005-09-12
forum: Server Platforms
---

### Post by guliver on 2005-09-12
[B]Does anybody know what should I add to this config file in order to let guest users (that belong to the same workgroup)  to access samba (public folder) without password?

This is my config file:[/B]

```
[global]


   workgroup = WORKGROUP
   security = user
   username map = /etc/samba/smbusers
   dns proxy = no
   log file = /var/log/samba/log.%m
   syslog = 0
   encrypt passwords = true
   passdb backend = tdbsam guest   
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
   netbios name = glavniserver
   socket options = TCP_NODELAY

[homes]

   comment = Home Directories
   browseable = no
   writable = yes
   create mask = 0700
   directory mask = 0700

[public]
   comment = Public Folder
   path = /home/public
   public = yes
   writable = yes
   create mask = 0777
   directory mask = 0777
   guest ok = yes
```

---

