---
title: "NFS kernel versus user package: Any other settings required?"
date: 2008-05-19
forum: Server Platforms
---

### Post by battista on 2008-05-19
I replaced my standard nfs-kernel-server package with the nfs-user-server package to be able to configure some uid/gid mappings to attach a mac to the system.

What I basically did, was to replace the two packages by uninstalling the first, rebooting and installing the second.

I have entries in /etc/exports like
```

/data   192.168.0.0/24(rw,no_root_squash,insecure,map_static=/etc/mac.map)

```
mac.map contains entries like
```

uid 501 1000
gid 501 1000
...

```

Everything seems to be fine from the log, except syslog says
```

Blocked attempt of 192.168.0.xx to mount /data

```

Did I miss any additional configuration requirements?

---

