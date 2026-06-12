---
title: "Finding suid programs on samba"
date: 2010-03-08
forum: Server Platforms
---

### Post by dragos2 on 2010-03-08
I am running some scans on a samba for invalid file names, times, etc.

Now I was searching for files which executes with root priviledges.
```

 find /home/samba -perm +6000 -print 2>/dev/null

```

And I found some, most of them are documents, are they dangerous ?

Also how can I filter to find only applications that executes with +6000 ?

---

