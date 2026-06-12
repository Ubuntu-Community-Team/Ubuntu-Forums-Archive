---
title: "encrypted home takes twice as much space"
date: 2012-02-07
forum: Security
---

### Post by gizmo the second on 2012-02-07
Dear Community,

It seems that when I encrypted my home with the new ubuntu 11, it made 2 identical copies, one mounted at normally at /home/user and one at /home/.encryptfs, such that it takes twice as much disk space, which caused my disk to be full.

I suspect this is virtual double space, since when I tried to delete some data in the encrypted section, it was immediately also deleted on my normal home, regrettably. Before I knew this, I tried eraising the /.encryptfs file brute force, including the file located at:

/home/user/.encryptfs/Private.mnt

Now I have a double problem since I can't login (apparently, maybe due missing Private.mnt file) and I've lost a lot of data.

Anyone remarks will be very much appreciated.

Cheers,
gizmo

---

