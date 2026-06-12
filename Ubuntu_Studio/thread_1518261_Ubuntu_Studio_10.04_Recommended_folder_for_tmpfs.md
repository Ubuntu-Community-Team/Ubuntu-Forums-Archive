---
title: "Ubuntu Studio 10.04: Recommended folder for tmpfs"
date: 2010-06-26
forum: Ubuntu Studio
---

### Post by nfidia on 2010-06-26
Hi,

I just read this here:

```
Low-Latency HOWTO

 ...and you definitely want to mount /tmp to tmpfs.

	none /tmp tmpfs defaults 0 0
```

From: [http://lowlatency.linuxaudio.org/](http://lowlatency.linuxaudio.org/)

Is this information applicable/useful for Ubuntu Studio 10.04?

If I apply the mount command on my machine, then I get among other this information:

> none on /dev type tmpfs (rw,mode=0755

Why is tmpfs mounted on the /dev folder, and not on the /tmp folder?

---

