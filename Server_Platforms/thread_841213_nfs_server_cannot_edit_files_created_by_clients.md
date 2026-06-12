---
title: "nfs server cannot edit files created by clients"
date: 2008-06-26
forum: Server Platforms
---

### Post by tr3s on 2008-06-26
hi!

i'm running ubuntu 7.10 and successfully set up a nfs server.

why are the files created by nfs clients have -rw-r--r-- and have 1000:1000 owner:group property in the nfs server mount folder? that's why they are not writeable by the nfs server.

this is what i have in /etc/exports:

```
/files 192.168.0.0/24(rw,async)
```

---

