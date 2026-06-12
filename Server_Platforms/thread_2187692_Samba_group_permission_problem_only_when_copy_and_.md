---
title: "Samba group permission problem only when copy and paste"
date: 2013-11-13
forum: Server Platforms
---

### Post by splater on 2013-11-13
Hi,

I have a samba server running on ubuntu 12.04. I have a share with the following config:
```

[share]
        valid users = @GROUP1
        read only = yes
        write list = @GROUP1
        path = /srv/samba/share/
        force group = GROUP1
        create mode = 0660
        directory mode = 0770

```

everything works well excepts that if someone from a windows machine copy and paste a directory from his local folder.

Here is a resume on the difference from a new folder or a paste folder:

```
drwxr-x---  2 user  GROUP1  4096 Nov 13 15:08 newFolder/
drwxrwx---  2 user  GROUP1  4096 Nov 13 15:07 pastedFolder/
```


pastedFolder should have group write permission.

With files there is not this problem.

Any clue? I tried the         force directory mode = 770
but it does not help ..

Thanks for your help.
Regards

---

### Post by volkswagner on 2013-11-15
What version of SAMBA are you using?

---

### Post by splater on 2013-11-17
It's version 3.6.3 running on Ubuntu 12.04

Any clue?
Thanks

---

### Post by splater on 2013-11-21
nobody has any idea?

thanks

---

