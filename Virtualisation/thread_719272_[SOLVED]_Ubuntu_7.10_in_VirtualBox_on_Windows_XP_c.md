---
title: "[SOLVED] Ubuntu 7.10 in VirtualBox on Windows XP: can't mount shared folders"
date: 2008-03-09
forum: Virtualisation
---

### Post by Lacrimstein on 2008-03-09
I installed Kubuntu 7.10 in VirtualBox on my dad's Windows XP work-issued laptop so he could run work-specific programs I wrote for him. Everything works fine, except mounting shared folders: when I type in the usual "sudo mount -t SharedFolder /path/to/mount/point", the command works fine; but when open it up in Dolphin, it says "/path/to/mount/point cannot be opened". One interesting thing: when the mount point directory has the same name as the shared folder, the mount fails and gives the "protocol error" error message. I have tried playing around with different mount options, such as changing uid and gid - but still no result. : (

---

### Post by Lacrimstein on 2008-03-09
Ok, I found a solution. Apparently, its a bug in the latest version of VirtualBox, 1.5.6. Installing 1.5.4 solved the problem

---

### Post by Lacrimstein on 2008-03-09
How do I mark the thead as solved? XD

---

### Post by fjgaude on 2008-03-09
Use **Thread Tool**s at near the top of the post.

---

### Post by Lacrimstein on 2008-03-09
lol I swear it wasn't there when I first looked
Thanks:lolflag:

---

