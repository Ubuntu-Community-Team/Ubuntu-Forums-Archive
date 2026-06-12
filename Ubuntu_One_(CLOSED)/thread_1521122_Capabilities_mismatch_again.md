---
title: "Capabilities mismatch again"
date: 2010-06-30
forum: Ubuntu One (CLOSED)
---

### Post by emakarov on 2010-06-30
Hi,

I have Xubuntu 9.10 Karmic on [Touch Book]("http://www.alwaysinnovating.com/touchbook/buzz2.htm") from Always Innovating, which runs on ARM processor. When I am trying to connect using Ubuntu One client, I get the "Capabilities mismatch" error described in [this thread]("http://ubuntuforums.org/showthread.php?t=1304850&highlight=capabilities+mismatch"). Apparently, this bug was solved by updating package ubuntuone-client - 1.0.2-0ubuntu1 to ubuntuone-client - 1.0.2-0ubuntu2.

However, my repositories have only ubuntuone-client - 1.0.2-0ubuntu1 package. The /etc/apt/sources.list file is the following.

```
deb http://ports.ubuntu.com/ubuntu-ports karmic main universe multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports karmic main universe multiverse
```

Also, I am reluctant to try 10.04 myself. As I understand, Always Innovating people (or volunteers) had to tweak 9.10 to make it work on Touch Book, and they are not done with 10.04 yet.

So, is there an updated version of ubuntuone-client package for this configuration?

Thanks,
Evgeny

---

