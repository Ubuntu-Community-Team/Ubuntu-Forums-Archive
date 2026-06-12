---
title: "compile wine with pulse audio support?"
date: 2011-03-26
forum: Wine
---

### Post by mons00n on 2011-03-26
Hi everyone, 

I'm currently running 10.04 x64 and a 'hacked' version of wine1.3 that allows me to play EverQuest using a few code changes found on winehq.  It's running pretty well, but when using Mangler the sound in game stops working after a while.  I've seen all of these precompiled wine+pulse ppas, but what I need is a method of compiling my version of wine to include pulse audio support.  I tried the winepulse packages but it ends with the resulting error:

```

configure: WARNING: libpulse 32-bit development files not found or too old, Pulse won't be supported.

```Which is mentioned on the winepulse website...but doesn't talk about how to resolve it.  Any ideas on how I might do this?  Thanks!

---

### Post by cogadh on 2011-03-26
Exactly what it says, you need to get the libpulse 32-bit development files. Just install the "libpulse-dev" package and that error should go away.

---

### Post by mons00n on 2011-03-26
> **cogadh said:**
> Exactly what it says, you need to get the libpulse 32-bit development files. Just install the "libpulse-dev" package and that error should go away.

I feel like an idiot, thanks so much for your help!

---

