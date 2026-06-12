---
title: "adduser home + additional directories"
date: 2008-07-06
forum: Server Platforms
---

### Post by kevmitch on 2008-07-06
In addition to users home directories in /home/$USER, we also keep a /nobackup/$USER directory on a separate partition for large data which is not backed up. 

The adduser script creates the /home/$USER directory just fine, but I would also like it to create the /nobackup/$USER directory automatically. I can't seem to find a way to do this short of directly modifying the adduser script or creating some sort of wrapper script. Is such messiness inevitable, or is there some proper/clever way to do this?

---

### Post by pdwerryhouse on 2008-07-07
You're in luck. At the end of the adduser script, it calls '/usr/local/sbin/adduser.local', if it exists.

This script should take four arguments: username, uid, gid and home directory.

Here's a very basic example to do what you want:

```
#!/bin/sh

mkdir /nobackup/$1
chown $1:$3 /nobackup/$1
```

---

### Post by kevmitch on 2008-07-07
Doh, that was in the man page. Don't know how I missed it! It seems that it also doesn't execute this script when called with the "--system" argument, which is conveniently the desired behaviour.

---

