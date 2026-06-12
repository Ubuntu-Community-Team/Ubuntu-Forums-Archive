---
title: "Wierd process"
date: 2008-04-14
forum: Security Discussions
---

### Post by RiazM on 2008-04-14
Past  couple of times I've booted I've noticed my cpu usage starting to go really high, and when i check htop it claims this is the thing:

 /usr/bin/X :o -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

I'm a bit worried because earlier there was an sshd process which was hammering my system that I didn't really know about. Anyone know what this is?

---

### Post by cdenley on 2008-04-15
That's just your X session. You can't have a graphical desktop environment without it.

---

