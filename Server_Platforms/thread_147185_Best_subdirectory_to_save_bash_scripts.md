---
title: "Best subdirectory to save bash scripts"
date: 2006-03-19
forum: Server Platforms
---

### Post by wgregori on 2006-03-19
I'm about to start learning how to write perl scritps... where is the most appropriate place to save them?

Thanks,
Wayne

---

### Post by nrwilk on 2006-03-19
I'd say either of these two:

If you want them to be accessible to all users:
```
/usr/share/bin
```
or
```
/usr/local/bin
```

If you want them to only be accessible to you, or if there are no other users and you want easy write permissions:
```
/home/wgregori/bin
```

for the second one, just make a bin directory under your home directory.

---

### Post by colo on 2006-03-20
System-wide available scripts should go to "/usr/local/bin", as it's in your users' PATH already. Drop your personal ones into "~/bin", and add that directory to your PATH, if you find to use them regulary.

---

### Post by StonePiano on 2006-03-20
[QUOTE=wgregori]... perl scritps... [/QUOTE]

It's starting to look like perl already.  You're a natural!

StonePiano ;)

---

