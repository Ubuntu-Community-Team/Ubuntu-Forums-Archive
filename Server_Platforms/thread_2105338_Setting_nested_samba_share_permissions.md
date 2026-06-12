---
title: "Setting nested samba share permissions"
date: 2013-01-15
forum: Server Platforms
---

### Post by malegria on 2013-01-15
Hello,

I am attempting to build a SAMBA file server for a classroom. I want students to be able to see the folder of their class period but only to be able to write in the folder I have created for them in that class period folder. I want this so that they will not destroy each others' work. 

Attached is my smb.conf 

This is the part I thought would serve that purpose:
```
[student work]
    browseable = no
    writeable = yes
    write list = %u
    path = /home/administrator/classes/1/%u
    create mask = 0755
    comment = Individual Student Work
    hide dot files = no
    valid users = %u,@admins
    force directory mode = 0777

```

where the %u variable would only allow them to enter the folder that matches their username.

I appreciate any guidance.

---

