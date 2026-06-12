---
title: "mounting NTFS over the network"
date: 2008-11-04
forum: Virtualisation
---

### Post by Tamaros on 2008-11-04
I'm running ubuntu x64 as a virtual machine using VMWare 6.5.0.

I am trying to mount one of the drives off the host machine as a network drive using```
mount -t smbfs //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword
```

I don't receive any errors but it seems to freeze up and I end up  having to <cntrl> + C out of it.

---

