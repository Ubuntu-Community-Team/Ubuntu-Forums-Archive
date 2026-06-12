---
title: "default file ownership"
date: 2006-08-08
forum: Server Platforms
---

### Post by mynameisjohn on 2006-08-08
hello the forum :-)

i setup ubuntu as a samba server with vscan and everything is working as expected.

problem is now that i could do with sharing the samba home shares over nfs too for our mac clients (they use an early osx which plain won't work with smb: home shares).

my permissions on the files and folders need to remain intact for the samba vscan to work, here is an example of a file from a users folder:

```
-rwxr-x--- 1 myuser   services  68 2006-08-08 12:26 eicar.com
```

is it possible to set the owner to be 'services' without adding it as the users primary group, and setup these file permissions when a new file is created over nfs?

if not i guess i'll need to write some sort of recursive script to run each evening, which seems drastic considering there's about 1tb of stuff on there...

thanks for any advice

mnij

---

