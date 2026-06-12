---
title: "Unionfs and full disk"
date: 2007-10-03
forum: Server Platforms
---

### Post by Frunktz on 2007-10-03
Hi!
I have a weird problem with unionfs.
Situation:
/dev/hda1 -> 80 GB on /media/Disk1
/dev/hdb1 -> 80 GB on /media/Disk2

/media/Union = Disk1=rw:Disk2=rw

df return always 80 GB on /media/Union
I think..no problem, unionfs have branch priority so when first disk is full, it automatically copy on second...
Well, it isn't. When first disk is full, error, Disk is full cannot write..

My question is: I'm wrong some mount option or unionfs don't switch when disk is full.

Ps:- I've tried also with AUFS and the behaviour is the same.

Thanks

---

### Post by GGLucas on 2007-12-25
Got here through a search, I have the same problem, is this possible or should I look towards more complex solutions like RAID or LVM ? I rather like UnionFS because it keeps both separate filesystems usable even if they're not mounted as a union.

I have a 320gb disk and a 330gb partition on another disk union mounted, the first disk has 800mb space left, and copying a 1gb file into the union mount will not move it to the other disk like expected (I could just create the folder in the empty disk and set it's priority higher, but I'd like it to work seamlessly)

---

