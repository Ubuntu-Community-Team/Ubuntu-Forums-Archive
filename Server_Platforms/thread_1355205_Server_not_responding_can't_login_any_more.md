---
title: "Server not responding/ can't login any more"
date: 2009-12-14
forum: Server Platforms
---

### Post by 2smooth on 2009-12-14
For some reason the web-server suddenly didn't respond anymore, also not after rebooting. I also can't connect via ssh.

It isn't also possible to login via the console. It seems like the password for the root user and a regular user has been reset.

And after a couple of minutes i get this error messages on the login screen of the console:

```
Out of memory: kill process 5899 (mysqld) score 442784 or a child
```

Also when i scroll back i see this kernelmessage:
```
mdadm: CREATE user root not found
```

Sombody tried to help me by telling grub to load init=/bin/bash

But he couldn't find all the partions, because i use LVM and the lvm driver isn't loaded.

What can i do now/try? How can i manually access/mount the LVM volumes for example with a live cd?

---

### Post by 2smooth on 2009-12-14
I've checked my system but it seems that the root password is gone?
Isn't it suppose to be in /bin or /sbin?

---

