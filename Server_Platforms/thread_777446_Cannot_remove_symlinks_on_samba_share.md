---
title: "Cannot remove symlinks on samba share"
date: 2008-05-01
forum: Server Platforms
---

### Post by shamael on 2008-05-01
Hallo, I have this problem with symlinks on a samba share: I can create them but not delete them. Obviously, I have full rights over the folder and I can create and delete regular files without issues.
Both rm and unlink report the deletion as successful but they don't actually do anything.
The shares are mounted through fstab with the following options:

```
 credentials=/etc/samba/shamael_credentials,rw,lfs,uid=shamael,gid=famiglia 
```


Needless to say, if I bypass samba by logging onto the server through ssh, I can remove the offending symlinks.

Any ideas?

Thanks!

---

### Post by shamael on 2008-05-10
Bump...

---

### Post by shamael on 2008-05-16
Bump!

---

### Post by sc0 on 2009-05-08
i'm seeing the same problem with a new set up but my client is running a much older version of ubuntu (5.04) while my samba server is running (9.04 server)

does it have anything to do with which version of cifs is installed on the client?

---

