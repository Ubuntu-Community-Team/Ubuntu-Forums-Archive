---
title: "/bin/bash permissions keep changing"
date: 2008-10-24
forum: Server Platforms
---

### Post by markprice on 2008-10-24
On our server the permissions on the /bin/bash file randomly change to:

```
-rwsr-xr-x
```

This prevents users' profile and bashrc scripts being run at login. The permissions should be -rwxr-xr-x but I can't figure out what could be causing this. We do have the root user enabled but that shouldn't cause any problems. Any ideas what could be causing this?

Thanks

---

### Post by bunnynuts on 2008-10-25
Did you chown root to something other than the default root:root and what setuid changes have you made? Did you chmod bash to 777 at some point?

---

### Post by markprice on 2008-10-27
No I haven't changed the user, group or userid on the file. I also have never set the permissions to 777. After it gets changed to -rwsr-xr-x, I go in and perform chmod 755 on /bin/bash to get it back to normal.

---

