---
title: "Directly access harddrive over network."
date: 2008-09-07
forum: Security
---

### Post by u-slayer on 2008-09-07
Hi, I want to remotely connect to an encrypted hard drive over NFS. I don't want the computer serving the drive to have access to the filesystem on it, just provide raw data access.

I tried mounting /dev on my NFS share so I could access /dev/sdc directly across the network:
```
/dev            192.168.1.1/24(fsid=1,rw,no_root_quash,async)
```

But when I go to access /mnt/server/sdc I get my machines harddrives's data instead of the remote machine's data. Is this even possible? Should I be using ssh instead?

---

