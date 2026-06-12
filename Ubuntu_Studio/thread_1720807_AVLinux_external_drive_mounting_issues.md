---
title: "AVLinux external drive mounting issues"
date: 2011-04-03
forum: Ubuntu Studio
---

### Post by Brendo613 on 2011-04-03
So I'm running AV Linux, which is Debian based, but I'm having no luck with my flash drive nor my external drive, both of which are functioning devices.  I get the error message "wrong fs type, bad option, bad superblock on /dev/sdb1."  What can I do to get USB drives to automount correctly?

---

### Post by Brendo613 on 2011-04-03
okay!  I can mount an external drive, but it's a stupid hack method.  The auto-mount option ubuntu offers, for example, is much more preferred than this elementary abuse of terminal.

```
mkdir /media/usb
mount /dev/sdb1 /media/usb
```

red.  neck.

---

