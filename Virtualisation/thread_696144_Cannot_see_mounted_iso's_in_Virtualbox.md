---
title: "Cannot see mounted iso's in Virtualbox"
date: 2008-02-13
forum: Virtualisation
---

### Post by meanerelk on 2008-02-13
I installed Ubuntu Server 7.10 on the latest version of VirtualBox OSE. (It's running the 368 kernel, because the server kernel doesn't work with VirtualBox).

I'm trying to install Guest Additions, but I cannot mount the ISO. I've tried mounting other ISO's too, and none of them work. VirtualBox says they are mounted, but there's nothing in /media/cdrom. 

```

ls -la
total 8
drwxr-xr-x 2 root root 4096 2008-02-13 12:09 .
drwxr-xr-x 4 root root 4096 2008-02-13 12:09 ..

```

I've searched the threads, but I haven't found the solution. Anyone have any similar problems?

---

### Post by meanerelk on 2008-02-13
Nevermind, I figured out a solution. If, after clicking "Install Guest Additions" you cannot see the iso, run 

```
mount /media/cdrom
```

and it will appear.

Incidentally, it needs the X server, so I won't be using it anyways. I really wanted to use shared files, so this is a bit of a disappointment.

---

