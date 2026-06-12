---
title: "Trying to launch a program, I get a python error"
date: 2019-11-27
forum: Server Platforms
---

### Post by leon.lain.delysid on 2019-11-27
Hello! It's been a while since I've been here.

I have a problem I can't solve.
```
$ nyx
Traceback (most recent call last):
  File "/usr/bin/nyx", line 6, in <module>
    from pkg_resources import load_entry_point
ModuleNotFoundError: No module named 'pkg_resources'
```

Can anyone help me?
Thanks for reading!

NB: I'm running Ubuntu Server 18.04 upgraded from 16.04

---

### Post by The Cog on 2019-11-27
I just checked on my 19.10, with **apt search pkg_resources** and I see these two packages that are installed: python-pkg-resources and python3-pkg-resources. Maybe you should check that those are installed on your system.

---

### Post by leon.lain.delysid on 2019-11-29
> **The Cog said:**
> I just checked on my 19.10, with **apt search pkg_resources** and I see these two packages that are installed: python-pkg-resources and python3-pkg-resources. Maybe you should check that those are installed on your system.

Thanks a lot! Installing python3-pkg-resources did it.

---

