---
title: "Bad file descriptor"
date: 2009-02-12
forum: Server Platforms
---

### Post by derjoerg on 2009-02-12
Hi,

I have a amd64-system running with hardy and kvm (also hardy-guests).

Yesterday one of the guests crashed and since then I have the following entry in my kern.log
```

kernel: Cannot read proc file system: 9 - Bad file descriptor

```

And since then I get "every" minute !!!! the following additional entry in kern.log
```

last message repeated 1746186 times

```

How can I solve this?

Thanks in advance

Joerg

---

### Post by derjoerg on 2009-02-16
What I also recognized is, that "klogd" and "syslogd" consume as much CPU as they can!


HELP!


Joerg

---

