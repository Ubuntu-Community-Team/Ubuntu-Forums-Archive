---
title: "File wned by gid 1001 should be 0"
date: 2011-02-11
forum: Server Platforms
---

### Post by Steff_NL on 2011-02-11
Dear,

I've got the following error message on my Ubuntu 10.10 Server after messing up the root permissions. 

```
/etc/sudoers owned by gid 1001 should be 0
```

I've found some threads on this forum but they do relate to Ubuntu Desktop while this is Ubuntu Server. Therefor I started a new thread. Hope you don't mind. 

I've tried the following command:

```
chown root:root /usr/bin/sudo
```
```
chmod 4755 /usr/bin/sudo
```

The first command works, the second returns error: No permission

Someone knows the answer to fix this? Thanks

---

### Post by Steff_NL on 2011-02-14
No one knows the solution?

---

