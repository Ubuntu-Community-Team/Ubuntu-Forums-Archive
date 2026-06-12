---
title: "Sync individual files?"
date: 2010-05-13
forum: Ubuntu One (CLOSED)
---

### Post by danh48176 on 2010-05-13
I decided I liked the idea of Ubuntu One for synchronizing my config files, such as ~/.vimrc.  However, the current client will only synchronize entire directories.  Is there a way to synchronize files without copying them into a synchronized directory?  I don't want to synchronize my entire home dir as that contains data I'm not comfortable having in the cloud.

I thought symlinks would be the answer, but learned that the client daemon ignores them.  I could copy files back and forth from a sync'd dir, but that requires active maintenance, and I'll eventually stop doing it.  I could also do things like "source Ubuntu\ One/.vimrc" from the real .vimrc, but not every program supports sourcing multiple config files.

Any thoughts? Has anyone else solved this?  Google didn't turn up much on this topic, so I appreciate the input.

Thanks!

---

### Post by joshuahoover on 2010-05-13
> **danh48176 said:**
> I decided I liked the idea of Ubuntu One for synchronizing my config files, such as ~/.vimrc.  However, the current client will only synchronize entire directories.  Is there a way to synchronize files without copying them into a synchronized directory?  I don't want to synchronize my entire home dir as that contains data I'm not comfortable having in the cloud.

I thought symlinks would be the answer, but learned that the client daemon ignores them.  I could copy files back and forth from a sync'd dir, but that requires active maintenance, and I'll eventually stop doing it.  I could also do things like "source Ubuntu\ One/.vimrc" from the real .vimrc, but not every program supports sourcing multiple config files.

Any thoughts? Has anyone else solved this?  Google didn't turn up much on this topic, so I appreciate the input.

Thanks!

I think the best solution right now is to place the config files in a folder synchronized by Ubuntu One and then symlink those to the normal config directory. I think this should work. I haven't tested it (yet) myself and am not sure if programs will like this "trick" or not. 

Thanks,

Joshua

---

