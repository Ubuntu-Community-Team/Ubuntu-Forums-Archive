---
title: "resync /dev/disk/by-label"
date: 2008-06-30
forum: Server Platforms
---

### Post by dummzeuch on 2008-06-30
Hi,

I unplugged a disk and plugged in a different one but /dev/disk/by-label (and the other subdirs as well) still show the previous disks.

I am now looking for a way to force udev to update the links preferablly without rebooting the server.

I did this before and it was updated automatically, so apparently I did something differently this time, but I couldn't say what.

Any hints?

twm

---

### Post by enoksrd on 2009-02-14
```

sudo /etc/init.d/udev restart

```

worked for me.

---

