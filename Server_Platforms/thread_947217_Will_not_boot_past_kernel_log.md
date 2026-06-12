---
title: "Will not boot past kernel log"
date: 2008-10-14
forum: Server Platforms
---

### Post by Technoviking on 2008-10-14
We have a dapper server that will not boot past the kernel log daemon startup. There is no obvious errors in the logs files. All the disk have space remaining, and fsck came up clean. The server had problems after being moved across campus.

Any ideas?

---

### Post by atoponce on 2008-10-14
I'd only be concerned about disk space, if you have /var on a separate partition. If so, then reporting disk space take two commands, not one:

```
df -h
```
```
df -i
```

If /var is full, it could out of blocks or inodes. Either could keep the kernel from flushing its logs to disk.

---

### Post by Technoviking on 2008-10-14
Plenty of disk space on var.

---

### Post by jpeddicord on 2008-10-14
Is the server set up for over-the-network logging, whether inbound or outbound? That would be my first thing to check, since a physical move probably resulted in new network settings.

---

