---
title: "Can just the folder structure be locked?"
date: 2008-10-17
forum: Server Platforms
---

### Post by endanderson on 2008-10-17
Sorry for the n00b question but I just setup my first Linux box (Ubuntu Server) and I am wondering:

Is there anyway to lock the folder structure of my samba file server so that no one accidentally moves folders around even though everyone can save and make new files.

Thank you
Edwin

---

### Post by lykwydchykyn on 2008-10-17
At the filesystem level there is a permissions option known as the "sticky bit".  If you set the "sticky bit" on a directory, only the owner of a directory may delete the directory, even though others may created, edit, and delete files inside it (if they have write permissions).

The command to set the sticky bit is:
```

chmod +t directory

```

You may have to play around with that to get the exact behavior you want, but I think if you made the directory structure owned by a single user, then set the sticky bit on all the folders, it should give you what you want.

---

