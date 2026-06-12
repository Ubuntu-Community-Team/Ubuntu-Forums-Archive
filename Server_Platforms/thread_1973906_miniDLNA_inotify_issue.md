---
title: "miniDLNA inotify issue"
date: 2012-05-05
forum: Server Platforms
---

### Post by Jademalo on 2012-05-05
I have no idea if this is the right place or not, but.. Eh.

I have a server installation of 12.04, and I have miniDLNA installed on it.
However, for some reason it does not automatically update with new files that I add to directories it scans.

I get this error when it loads - 
```
[2012/05/05 02:02:26] inotify.c:182: warn: WARNING: Inotify max_user_watches [16364] is low or close to the number of used watches [252] and I do not have permission to increase this limit.  Please do so manually by writing a higher value into /proc/sys/fs/inotify/max_user_watches.

```

I have already tried increasing the default, but I am out of ideas. It just doesn't update when I add new things.

Does anyone know what I can do? =/

---

### Post by ozzman2 on 2012-05-08
I read somewhere on another forum to edit
/proc/sys/fs/inotify/max_user_watches
and   change
8192 to 65536

Not really sure if it   does anything or not though...

---

