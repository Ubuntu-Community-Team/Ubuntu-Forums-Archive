---
title: "USB drive automatically unmounts"
date: 2011-05-20
forum: Server Platforms
---

### Post by alexlaban on 2011-05-20
I've got a problem, a while a go I ran out of both SATA ports and PCI expansion slots in my Ubuntu (home) Server and I also ran out of storage space, as I needed more space I popped in a 2TB drive via USB, formatted and added to FSTAB hoping that it would work like a normal drive (a very slow one but still work).

However it seems like every now and then the server for some unknown reason unmounts the physical drive so that I can't access it, if I try to access it via SAMBA I just see an empty folder. 

This is what the entry in my FSTAB looks like
```
UUID=553e93eb-f0f1-4f4f-ac81-7e351b6b99c9    /home/share/e2000GB   ext4    defaults     0        2

```

---

