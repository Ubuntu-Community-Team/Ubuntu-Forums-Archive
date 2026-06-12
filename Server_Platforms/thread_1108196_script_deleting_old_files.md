---
title: "script deleting old files"
date: 2009-03-27
forum: Server Platforms
---

### Post by chewbakka on 2009-03-27
Hello forum,

i´m in the need of deleting old files (example older than 7 days) in folder hierarchy recursively. So far not the big problem i found enough stuff on the web like:

```
find /samba/path/ -name 'whatever*' -type f -daystart -ctime +7 -exec rm -f {} \;
```

but this also deletes the folders that i need to keep.
Any idea how i could delte the old iles with keeping the folders?

thanks in advance

---

### Post by chewbakka on 2009-04-01
hello,

tmpwatch did the trick. took the fedora rpm and made an deb out of it (with alien  -k). works like a charm.

---

