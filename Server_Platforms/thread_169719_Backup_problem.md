---
title: "Backup problem"
date: 2006-05-03
forum: Server Platforms
---

### Post by soon82 on 2006-05-03
I had setup my ubuntu as a samba server currently...It is very stable..

Now i had problem to backup all my data inside the samba server...

anybody can tell me.. how to backup my data from my server....

Thank You...

---

### Post by geek.de.nz on 2006-05-03
I personally like dd backups. You can just backup a partition like that, but I don't know if you want that. E. g.
```

sudo -l
#enter password
dd if=/dev/hda1 of=backup_of_hda1.dd

```

Otherwise, just have a look around with apt-cache:
```

apt-cache search backup

```

Hope that helps. If not please explain the problem more elaborate. Where do you want to backup to? etc.

---

