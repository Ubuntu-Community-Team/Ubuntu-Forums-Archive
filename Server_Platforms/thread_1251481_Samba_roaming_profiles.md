---
title: "Samba roaming profiles"
date: 2009-08-27
forum: Server Platforms
---

### Post by rentacop on 2009-08-27
Hey guys, I configured samba with roaming profiles. Everything is working fine, however i would like to change where samba saves the user data.

Currently samba is saving the data and profiles like so

data   : /home/USER_NAME/
profile: /home/USER_NAME/Profiles


What i would like to do is save to the following location

/media/data/student/USER_NAME (for files)
/media/data/student/profiles/USER_NAME

Tried changing both logon path and logon home to the above paths and it could no longer locate my default profile (netlogin/Default user)

Thanks

Heres my current config.

```

   
   workgroup = me.local
   security = user
   domain logons = yes
   logon path = \\%N\%U\profile
   logon drive = H:
   logon home = \\%N\%U
   logon script = logon.cmd

[homes]
   comment = Home Directories
   browseable = no
   read only = no
   create mask = 0700
   directory mask = 0700
   valid users = %S

[netlogon]
   comment = Network Logon Service
   path = /media/data/netlogon
   guest ok = yes
   read only = yes
   share modes = no



```

---

### Post by rentacop on 2009-08-28
bump

---

### Post by rentacop on 2009-09-01
I figured it out. I was mounting a NTFS drive, It appears that root is the only user with permission to modify ntfs.

---

