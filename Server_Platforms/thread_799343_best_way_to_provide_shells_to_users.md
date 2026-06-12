---
title: "best way to provide shells to users?"
date: 2008-05-18
forum: Server Platforms
---

### Post by rycole on 2008-05-18
i'm looking for the best way to give a client a shell account that has a maximum space quota. currently, i was thinking about creating a virtual file system by the commands: dd, mkfs and mount. this allows me to easily specify the size of the user's disk image, as well as easily relocate and remove it if necessary. this also makes it easy for assigning users to groups, and giving groups permissions to the virtual file system. to keep the users confined to their vfs, i was going to use a chroot environment. i haven't tried the chroot out, yet, but i've read about it and it sounds like something that'd keep them in thier directory.

i wouldn't modify fstab, i'd just have a script that'd mount all of these. (i think this would give me finer control over the system)

is this a good way to do this, or is there a better way?

thanks in advance

---

