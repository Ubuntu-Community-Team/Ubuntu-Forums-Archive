---
title: "ssh and ulimit -n issue"
date: 2011-02-11
forum: Security
---

### Post by cnkbrown on 2011-02-11
I have an init script running as a special build user which performs an automated build that fails with (Too many open files).

I updated /etc/security/limits to allow the special user more open files, but that didn't work - the init script still isn't allowed more open files.

Here's a demonstration of the problem;

```
$ su - sbsbuild -c "ulimit -n"
Password: 
1024
$ ssh sbsbuild@localhost 'ulimit -n'
sbsbuild@localhost's password: 
32768
```

How do I craft the 'su' command so that 'ulimit -n' gives the same result as the 'ssh'?

---

### Post by cnkbrown on 2011-04-14
bump

---

