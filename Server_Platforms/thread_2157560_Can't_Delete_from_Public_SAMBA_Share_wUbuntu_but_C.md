---
title: "Can't Delete from Public SAMBA Share w/Ubuntu but Can from Windows"
date: 2013-06-25
forum: Server Platforms
---

### Post by kendoori on 2013-06-25
Am trying to create a public SAMBA file share that allows both Windows and Ubuntu users to read/write/delete/create files and folders.

Windows users can read/write/delete with no issues. An Ubuntu guest, can create, but can't modify or delete files.

I'm mounting the share as follows in my fstab

```
//192.168.0.5/storage /home/foo/Shares/TK-Public/ cifs rw,guest,noperm 0 0
```

I unmounted my shares and did a 
```

sudo chmod -R 777 ~/Shares
```

and then remounted.

Here's my SAMBA config

```
[storage]
    create mask = 0777
    directory mask = 0777
    browseable = yes
    comment = Public Share
    writeable = yes
    public = yes
    path = /srv/storage
        force user = nobody
        force group = nogroup

```

---

