---
title: "Which mount parameters should I use for external ext3?"
date: 2009-11-04
forum: Server Platforms
---

### Post by everdred on 2009-11-04
I have a small home media server running Ubuntu Server 9.10, with all the good stuff (media) stored on an external USB hard drive, on an ext3 partition of almost 1 TB. The partition is almost constantly in use, reading and writing small amounts of data.

Could anyone suggest which mount parameters I should be using for this? At the moment, the mount looks like this:

```
/dev/sdb6 on /stuff type ext3 (rw)
```

and the line in my fstab is

```
UUID=... /stuff ext3 defaults 0 0
```

Any insight into what I should be doing would be greatly appreciated.

---

### Post by everdred on 2009-11-23
[bumping thread]

---

