---
title: "Chroot"
date: 2005-10-18
forum: Server Platforms
---

### Post by dbee on 2005-10-18
I can't chroot ???

root@ubuntu:/home/babo/Desktop/php-5.0.5 # chroot /chroot /bin/bash
chroot: cannot run command `/bin/bash': No such file or directory

root@ubuntu:/home/babo/Desktop/php-5.0.5 # stat /bin/bash
  File: `/bin/bash'
  Size: 643852          Blocks: 1272       IO Block: 4096   regular file
Device: 301h/769d       Inode: 2223933     Links: 1
Access: (0755/-rwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2005-10-18 13:47:35.591787312 +0900
Modify: 2005-01-14 06:44:11.000000000 +0900
Change: 2005-09-30 22:40:15.000000000 +0900

---

### Post by LordHunter317 on 2005-10-18
Is /bin/bash in the chroot?  If not, you won't be running that in the chroot.

---

### Post by dbee on 2005-10-19
oops !

---

