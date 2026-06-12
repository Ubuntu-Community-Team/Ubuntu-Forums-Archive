---
title: "samba access question"
date: 2007-08-12
forum: Server Platforms
---

### Post by db9s on 2007-08-12
I have set up a samba server where all users can access files. But I also have some folders which certain users can access and I managed to do it by:
```

[linuxBU]
path = SOME_PATH
browseable = yes
read only = no
guest ok = no
valid users = USERNAME1
create mask = 0600
directory mask = 0700
force user = USERNAME1
force group = USERNAME1

```

What is weird is the 'valid users' field. Does this mean that anyone can spoof the USERNAME1 from a windows account and access the files :(
My only point here is that users will need to use the correct samba username & password to have read, write & execute permissions. Otherwise they get to see nothing.  Am I doing it correctly? The 'valid user' field is giving me a false sense of security.

Thanks

---

### Post by codmate on 2007-08-12
No - usually the user will have to type a username and password when trying to access the share from their windows box.

Set this password by using ```
smbpasswd
```.

---

