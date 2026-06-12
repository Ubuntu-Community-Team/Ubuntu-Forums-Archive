---
title: "How get debug symbols for apache2?"
date: 2009-07-30
forum: Server Platforms
---

### Post by christian.convey on 2009-07-30
I've got an 8.04 server running Apache 2.2.8-1ubuntu0.5.  

I'm trying to debug an apache2 server that hangs every few days or so, and I'm following these directions:
[http://prefetch.net/articles/debuggingapache.html](http://prefetch.net/articles/debuggingapache.html)

Those directions have me call "gcore" or "pstack" on the running (and hanged) apache2 process.  The idea is that by looking at the stack trace, I'll get some insight into what's going wrong.

The problem is, the Ubuntu 8.04 packaging of apache2 doesn't seem to include debug symbols, so the stack trace is pretty useless to me.

Does anyone know how I can get access to the debug symbols needed to interpret the stack trace properly?

Thanks,
Christian

---

### Post by Gloves on 2009-10-23
Hi Christian,

I've got a similar problem, but on Jaunty, did you ever find out where to get the debug symbols from?

Thanks
Hans

---

### Post by christian.convey on 2009-10-23
Our ultimate solution was to buy a new computer (we had concerns about the old computer's hardware), and installed 9.04.

So I'm afraid I never solved this in a way that would help you.

---

### Post by __p1n__ on 2009-10-23
> **christian.convey said:**
> I've got an 8.04 server running Apache 2.2.8-1ubuntu0.5.  

I'm trying to debug an apache2 server that hangs every few days or so, and I'm following these directions:
[http://prefetch.net/articles/debuggingapache.html](http://prefetch.net/articles/debuggingapache.html)

Those directions have me call "gcore" or "pstack" on the running (and hanged) apache2 process.  The idea is that by looking at the stack trace, I'll get some insight into what's going wrong.

The problem is, the Ubuntu 8.04 packaging of apache2 doesn't seem to include debug symbols, so the stack trace is pretty useless to me.

Does anyone know how I can get access to the debug symbols needed to interpret the stack trace properly?

Thanks,
Christian

Download the source and rebuild.  Be sure to alter the link flags to include symbolic debugging information.

---

### Post by diesch on 2009-10-23
See [https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)

---

### Post by christian.convey on 2009-10-23
> **diesch said:**
> See [https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)

iirc, when I did this, the packages providing debug symbols had slightly different package version numbers than the actual Apache packages.  So I didn't install them out of concern that the debug symbols would be misleading.

---

