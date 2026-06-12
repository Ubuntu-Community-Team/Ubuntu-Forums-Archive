---
title: "NTbackup vs rsync with rdiff"
date: 2007-05-02
forum: Server Platforms
---

### Post by himurakenshin on 2007-05-02
Could someone please explain to me which is a better backup software? It seems like they both do similar tasks, granted one is for windows only, but which one performs better or has better features?

A response as soon as possible would be really appreciated.
Thanks very much.

---

### Post by Frosty Cold Drink on 2007-05-02
If you are just syncing directories, I'd tend to say rsync. rsync doesn't offer all of the backup options NTBackup does.

If you want some insane backup, check out [amanda]("http://www.amanda.org/"). Me? I'm a fan of throwing filesystems into svn, then backing that up. There are some downsides, though.

---

