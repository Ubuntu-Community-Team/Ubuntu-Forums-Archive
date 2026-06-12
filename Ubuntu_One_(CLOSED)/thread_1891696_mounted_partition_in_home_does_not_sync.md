---
title: "mounted partition in /home does not sync"
date: 2011-12-06
forum: Ubuntu One (CLOSED)
---

### Post by Chiel92 on 2011-12-06
Hello all,

I want to synchronize a ntfs partition that I mounted in my home folder.
I read about other people stumbling upon problems with syncing a partition as they tried to use symlinks. But this is a different story and I just don't know why this doesn't work.
I added these lines to /etc/fstab:

```
#We want to have the data partition always mounted
/dev/sda5   /media/Data ntfs    default,user,nls=utf8,umask=000,uid=1000    0   0
#We bind the Music folder in data to the Music folder in home, for the sake of Ubuntu One
/media/Data/Music       /home/user/Music   none    bind    0   0
```I can freely access the folder Music in my home, and it just looks like its a folder.
But Ubuntu one refuses to synchronize it.

Any ideas?

Regards

---

### Post by Chiel92 on 2011-12-15
The problem is kind of solved.
Today I use Ubuntu 10.04 again, instead of 11.10.
It appears that Ubuntu One neatly synchronizes the partition now.:P
But I have no idea why.

---

