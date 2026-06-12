---
title: "Space-ridden fstab smb entries"
date: 2006-08-25
forum: Server Platforms
---

### Post by jmacaulay on 2006-08-25
I've got an smb network share that I'm connecting to, and the share's name has a space in it. I followed the advice here:

[http://ubuntuforums.org/showthread.php?t=27823](http://ubuntuforums.org/showthread.php?t=27823)

...and so I'm typing \040 in place of the space in the share name. It mounts fine, but the problem I'm having is that any time I do mount -a, the share gets mounted *again* at the same mount point. When I list my mount points, the same smb entry shows up once for every time fstab has been used to mount it, and I have to run umount that many times in order to actually unmount it.

Is there a good workaround for this? I'd rather not have to do a 'umount' after every 'mount -a'.

---

