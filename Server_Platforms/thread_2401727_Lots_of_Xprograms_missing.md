---
title: "Lots of Xprograms missing?"
date: 2018-09-21
forum: Server Platforms
---

### Post by warmango on 2018-09-21
So... im trying to install desktop software that i plan on using Via X-Fowarding via ssh on my ubuntu server, (18.04) but it keeps giving errors like this
```
bunny@code_merith:~$ sudo apt install xtermReading package lists... Done
Building dependency tree
Reading state information... Done
Package xterm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'xterm' has no installation candidate
bunny@code_merith:~$

```

---

### Post by TheFu on 2018-09-21
[https://launchpad.net/ubuntu/bionic/+package/xterm](https://launchpad.net/ubuntu/bionic/+package/xterm)

If that package doesn't exist, check that the package list us updated and that package repos are available.
I haven't tested 18.04 and don't have an install, but that is what I'd do under the same situation.  It does appear that "xterm" is the correct package name, at least to me.

---

### Post by warmango on 2018-09-21
I have checked that, it appears to have gnome-terminal insalled already, but when i run it, absolutely nothing happens. I have tested to see if my x-server on my laptop works (it does) but its not doing anything

---

### Post by TheFu on 2018-09-21
Exact command used?

---

