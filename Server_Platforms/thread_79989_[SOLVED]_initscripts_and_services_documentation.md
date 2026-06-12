---
title: "[SOLVED] initscripts and services documentation"
date: 2005-10-21
forum: Server Platforms
---

### Post by tcort on 2005-10-21
I just setup a Ubuntu 5.10 (ppc) server and I am looking for documentation on configuring the ubuntu init system from the command line (starting/stopping services, adding/removing services to start at boot, etc). It should look something like the [Gentoo Handbook: Initscripts]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=4") document, but for ubuntu.

Thanks!

---

### Post by tcort on 2007-10-19
This post has no replies :( It seems to come up in search results (95+ views). I guess I'll answer this one for myself and anyone who searches the forums ;)

> starting/stopping services
```

$ sudo /etc/init.d/xxx start
$ sudo /etc/init.d/xxx stop

```

> adding/removing services to start at boot
```

$ sudo update-rc.d xxx defaults
$ sudo update-rc.d -f xxx remove

```

---

