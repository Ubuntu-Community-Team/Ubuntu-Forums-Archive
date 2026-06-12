---
title: "fstab changes folder permissions"
date: 2006-11-11
forum: Server Platforms
---

### Post by doogy2004 on 2006-11-11
Here are the permissions that I have set on the Virtual Machines folder:
```

user@ubuntu:/var/lib/vmware$ ls -all
total 12
drwxr-xr-x  3 root root 4096 2006-11-10 15:08 .
drwxr-xr-x 21 root root 4096 2006-11-10 15:08 ..
drwxrwxr-x  1 root user 4096 2006-11-10 23:47 Virtual Machines

```

after I attempt to mount a network share on that folder via sudo mount -a or restart it changes the permissions to:
```

user@ubuntu:/var/lib/vmware$ ls -all
total 12
drwxr-xr-x  3 root root 4096 2006-11-10 15:08 .
drwxr-xr-x 21 root root 4096 2006-11-10 15:08 ..
drwxr-xr-x  1 root user 4096 2006-11-10 23:47 Virtual Machines

```

This leads to problems when I try to write to this folder.  It will not allow me to create things.

here is a copy of the line in my fstab:
```

//fileserver/ubuntu /var/lib/vmware/Virtual\040Machines smbfs defaults,errors=remount-ro,credentials=/root/.smbcredentials,uid=root,guid=user 0 0

```

If I use dmask=775,fmask=775 or even umask=775 it still does not change set the correct permissions that I want.

What can I do to have the correct owner and group with the correct permissions on this folder after the network share is mounted?

Thanks

---

