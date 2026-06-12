---
title: "Loosing uid and gid migrating from CentOs to Ubuntu"
date: 2011-05-22
forum: Server Platforms
---

### Post by vroby67 on 2011-05-22
I'm migrating a server form CentOs to Ubuntu 11.04. I migrated the users, moving the config files and gaining the access prompt for all the users just when I modified adduser.conf and login.defs, changing valid uid and gid to start from 500 instead of 1000.
When I try to copy the files from old server to the new one, either with rsync or cp -br, the system set to 0 uid and gid. If I explore the mount point, connected with sshfs, I can see the correct configuration, either as names or as numeric data.

---

### Post by ajgreeny on 2011-05-22
This should work, but I've never used it so make sure you back up all first, just in case it all goes to worms.
To get your uid/gid in linux you type ```
id
```To change your uid and gid, use the following command, which may need sudo```
usermod -g xxx -u xxx username
```where 'xxx' are the numbers you want to change to.

---

