---
title: "Run a simple one-line command on boot"
date: 2011-11-25
forum: Server Platforms
---

### Post by sirgad on 2011-11-25
Hi,

Ubuntu 11.10 Server 64-bit on a Dell E5400 laptop.

I'd like to have my laptop automatically disable its display on boot, prior to login, using the following command:

```
vbetool dpms off
```

It needs to run as root.  How would this be accomplished best?

Many thanks :)

---

### Post by btindie on 2011-11-25
```
$ sudoedit /etc/rc.local
```

---

### Post by sirgad on 2011-11-25
Yes, entering this command on a line on its own does the trick.

Many thanks.

---

