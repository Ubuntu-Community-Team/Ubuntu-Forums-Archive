---
title: "Help on installing packages without X"
date: 2008-04-17
forum: Server Platforms
---

### Post by itsnotvalid on 2008-04-17
Lately I tried to install mercurial by "sudo aptitude install mercurial" on Ubuntu 7.10 Server.
However as you know there is no "X windows" on server editon, at least it shouldn't be. But mercurial, as far as I know is a python based console apps, its dependencies includes x* packages, which adds up to 1xx dependencies on my installation.
So is there any way to just install console version of mercurial?

---

### Post by cdenley on 2008-04-17
Try this
```

sudo aptitude -R install mercurial

```
The package recommends tk8.4, but it is not a required dependency.

---

