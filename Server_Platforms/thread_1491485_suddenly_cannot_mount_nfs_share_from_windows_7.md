---
title: "suddenly cannot mount nfs share from windows 7"
date: 2010-05-23
forum: Server Platforms
---

### Post by ducky101 on 2010-05-23
I recently reinstalled my file server (moved from fedora to ubuntu server).

Now I cannot mount my nfs share from windows 7, mounting from mac osx works fine. 

In windows I either keep getting "the semaphore timeout period has expired" or "an unexpected error has occured".

Does ubuntu need some special magic to allow windows 7 to mount an nfs share?

This is my exports file 
```
/home/ducky101/ 	192.168.1.*(rw,sync,insecure,no_root_squash)
/home/ducky101/mnt/EXTRN2 192.168.1.*(rw,sync,insecure,no_root_squash)
/home/ducky101/mnt/EXTRN3 192.168.1.*(rw,sync,insecure,no_root_squash)

```

---

### Post by ingeva on 2010-05-23
> **ducky101 said:**
> Now I cannot mount my nfs share from windows 7, mounting from mac osx works fine.Sorry I can't answer your question. I had no idea that Windows could connect to an NFS system. I was looking because I also have an NFS connect problem.
Should a Windows XP system also be able to do that? In that case, what do we need Samba for? :)

---

### Post by ducky101 on 2010-05-23
Yeah windows can mount nfs shares. 
In vista and windows 7 you have to install Client Services for NFS under Add/Remove Software in the Control Panel. And I think the same goes for windows xp (can't really remember).

I actually don't use windows, haven't used it since windows xp service pack 1. My girlfriend uses win7 and my file server to stream tv shows from the nfs share which now doesn't work anymore :mad:.

As for samba, I had to use it only once to setup printer sharing I think under Red Hat Linux 7.0 many many years ago. Apart from that I never needed samba.

---

### Post by ducky101 on 2010-05-24
Anyone.... please :(

---

