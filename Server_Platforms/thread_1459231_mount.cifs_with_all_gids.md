---
title: "mount.cifs with all gids"
date: 2010-04-21
forum: Server Platforms
---

### Post by dragos2 on 2010-04-21
Regarding this cifs mount:

```

 mount.cifs //samba/samba /home/dragos/samba -o credentials=/.cred,uid=dragos,gid=20,40,50

```

user dragos in samba server is part of many groups, how can I make the mount aware of this ? I tryed adding more ids in gid like gid=20,40,50 but does not seem to be aware of that and it takes the first one.

Is there a solution for this or I should just drop all this and use nfs with the same ids and gids on both servers ?

---

