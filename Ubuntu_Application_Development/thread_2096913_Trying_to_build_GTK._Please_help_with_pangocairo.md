---
title: "Trying to build GTK. Please help with pango/cairo"
date: 2012-12-21
forum: Ubuntu Application Development
---

### Post by joblafors on 2012-12-21
Hello.
As title suggests I'm trying to compile GTK+.
Right now I'm stuck with dependencies - pango/cairo

I seemed to make and install cairo without any problems, but I'm stuck with pango.

when configuring I get this error :
```

checking for CoreText availability... no
checking for CAIRO... yes
checking which cairo font backends could be used... none
configure: Disabling cairo support
configure: error: *** Could not enable any backends.
*** Must have at least one backend to build Pango.

```
I googled for this problem and tried few solutions, but didn't manage to get this fixed.

Here is full config output.. *[PasteBin]("http://pastebin.com/raw.php?i=TdDw5Z1b")*

Pango version : 1.32.5
Cairo version : 1.12.8
Ubuntu 12.04

Please let me know for any additional info.
Thank you for any help

---

### Post by joblafors on 2012-12-21
So I just installed "gnome-core-devel" this seemed to do the job.

---

