---
title: "changing rcS shell"
date: 2010-04-26
forum: Security
---

### Post by chudder on 2010-04-26
Hi,

I'm trying to change the SHM memory block limits, to give some background, go to this thread for Avast

[http://forum.avast.com/index.php?topic=57775.0](http://forum.avast.com/index.php?topic=57775.0)

I can type in the code and it works fine but I have to do it every session.  Supposedly "Place those lines to /etc/init.d/rcS" but I don't know how to modify the rcS shell as root.  

Any ideas?

Thanks

chudder

---

### Post by cdenley on 2010-04-26
```

echo kernel.shmmax = 128000000|sudo tee -a /etc/sysctl.conf

```

---

