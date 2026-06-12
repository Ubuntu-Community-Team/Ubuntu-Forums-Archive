---
title: "Samba permissions + mounting the shares"
date: 2017-05-31
forum: Server Platforms
---

### Post by Nik2013 on 2017-05-31
Hi there. Is there a way to make a samba user account read and execute only? I've seen that theres a read list option on the share level access options for samba. What I'm trying to do is access my shares from 1 ubuntu system running samba to another running plex (And some other services on top) and give the plex process the minimum permissions to run the files properly.

1 other question. Whats the most correct way / syntex for auto mounting samba shares in fstab? I've seen some examples where I think people setup a credentials file that they use for getting authorised in fstab. Something like this I think:

```
//server/share /pathto/mountpoint cifs credentials=/home/username/.smbcredentials,uid=shareuser,gid=sharegroup 0 2
```

Thanks for any help.

---

### Post by wildmanne39 on 2017-05-31
*Thread moved to **Server Platforms**.*

---

