---
title: "nfs mount permission denied"
date: 2008-01-30
forum: Server Platforms
---

### Post by tronica on 2008-01-30
i have a server runing 7,04 and i setup nfs. I've done this previously before on 6.06.  I setup up /etc/exports with 
```

/media/Storage 192.168.1.1/24(rw,no_root_squash,async)

```

then i restart nfs with

```
sudo /etc/init.d/nfs-kernel-server restart
```

when i try to mount it from another box i get
```

mount: 192.168.10.10:/media/Storage failed, reason given by server: Permission denied


```

not sure what to do, i think im just overlooking somthing. Any help is greatly appreciated.

I got it going, just needed to add my other box into /etc/hosts on the server.

---

