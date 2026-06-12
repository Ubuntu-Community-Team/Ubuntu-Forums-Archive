---
title: "CIFS Folder using Likewise Open"
date: 2008-10-20
forum: Server Platforms
---

### Post by moffa on 2008-10-20
Hello,

I've setup likewise open and I can SSH using my AD credentials but I can not actually get into my folder.

```

sudo mount -t smbfs -o username='UEC\myusername' //UEC.local/DFS/LD /home/UEC/myusername/ld

```

but when I go to /home/UEC/myusername/ld I can only see the shares on UEC.local/DFS not DFS/LD.  When I try to go into the LD folder I see the console change paths but the folder does not actually move.
```
myusername@comptuername:/home/UEC/myusername/ld/LD$
```

Any idea why I can not browse the folder? My AD account has access to LD but not the other folders.

---

