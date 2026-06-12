---
title: "HELP! Deleted /boot contents..."
date: 2012-09-11
forum: Server Platforms
---

### Post by danbishop on 2012-09-11
Ok, really, really silly thing to do... but I've accidentally deleted almost everything in /boot leaving only the grub folder and the memtestx86 image intact.

Is it possible to regenerate /boot from the running system?

I tried reinstalling linux-image-server and linux-headers-server but this didn't seem to help...

Any help is VERY much appreciated!

---

### Post by danbishop on 2012-09-11
Might have cracked it...

```
sudo apt-get install --reinstall linux-image-2.6.32-42-server
```

Replacing version with your own kernel version of course...

---

### Post by danbishop on 2012-09-11
It worked! :D

---

