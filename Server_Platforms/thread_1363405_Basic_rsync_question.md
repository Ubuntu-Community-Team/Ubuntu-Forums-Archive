---
title: "Basic rsync question"
date: 2009-12-24
forum: Server Platforms
---

### Post by kenquad on 2009-12-24
Hi all:

I am implementing rsync to do a simple local hd to local hd backup on my server.  This is my first time using the program.  I understood that, by default, rsync copies only files with changes, i.e.
```
rsync --recursive --delete /dir1 /backup/dir1
```
would copy only changed files, and only those parts of the files which changed.  This may be what is happening; however, I tried running that rsync command twice in a row with the --verbose and --stats switches, and it seemed to be copying everything over again.  I checked this via modified time on files which had already been backed up, and they showed modified at the time of the second backup (they hadn't changed from the first).

Question 1: How do I tell if this is running correctly?
Question 2: If it isn't, what have I done wrong?

Thanks!

---

### Post by msw on 2009-12-24
Try:
```

rsync -avz --recursive --delete /dir1 /backup/dir1

```

---

