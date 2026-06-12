---
title: "Deleted Files Not Going To Trash!!! (disk space being eaten)"
date: 2009-08-19
forum: Server Platforms
---

### Post by antdgar on 2009-08-19
Ubuntu server 9.04

Well I just deleted 50GB of files and I noticed that my 'free space' did not change.
I've narrowed down the problem, it is that deleted files are not going to the trash can!

The files disappear from their original location, and searching for the file yields no results. But the problem is 'free space' is not changing.

The weird thing is, if I delete one file at a time, it may go to the trash can. But if I delete a whole load of files, they wont go to the trash can :-s

It's saying I'm using 150GB, but I'm definitely not, I'm only using around 40GB.

Please can someone help me truly delete these files? My server is slowly running out of space because of this issue.

---

### Post by smeerbartje on 2009-08-19
Does the server editional has a trashcan??

---

### Post by Grim76 on 2009-08-19
I had something similar happen on a USB memory key. Try looking for a .trash folder.  Keep in mind that the . makes the file a hidden file.

---

### Post by wojox on 2009-08-19
If your running gnome on a server are you deleting as root?

```
gksudo nautilus '/root/.Trash/'
```

Look in there.

---

### Post by smeerbartje on 2009-08-20
Can someone please explain to me if (and where) the server edition uses a trash bin?

---

