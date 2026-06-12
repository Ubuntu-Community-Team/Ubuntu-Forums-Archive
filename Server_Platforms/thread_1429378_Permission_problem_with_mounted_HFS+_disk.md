---
title: "Permission problem with mounted HFS+ disk"
date: 2010-03-14
forum: Server Platforms
---

### Post by germ65 on 2010-03-14
Hello,
     I have an external USB drive, formatted as Mac OS Extended, that I mount at /mnt/arca using the following fstab entry:

```

/dev/sf2     /mnt/arca       hfsplus        user,noauto      0       0
```

Mounting goes OK and I can move files into the /mnt/arca directory using Webmin file mananger.

However, /mnt/arca belongs to root (uid=99). If I try to chown it to myself (uid=1000), it reverts to 99 upon execution of the mount command. 

I have tried to add gid=1000 to the options above, but the same happens. 

How can I mount the external drive so that I have write/read privileges on it?

TIA,
Davide

---

