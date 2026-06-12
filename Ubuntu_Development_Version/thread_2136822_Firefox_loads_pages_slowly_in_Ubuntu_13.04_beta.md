---
title: "Firefox loads pages slowly in Ubuntu 13.04 beta"
date: 2013-04-18
forum: Ubuntu Development Version
---

### Post by IdoSC on 2013-04-18
Hello,

I've recently upgraded my Ubuntu to 13.04 beta. As a big enthusiast of Firefox, I booted up Aurora and noticed a weird pattern where navigating to a page results in the tab loading (while displaying a blank page) for quite a long time, then the page just appears at once. I'm currently writing from Chrome, where it doesn't happen - the page loads instantly. Speed tests from my PC on Firefox (once it finally managed to load the speed test's website), Chrome and on other PC's shows my supposed download speed precisely, 20 Mbps.

The problem persisted when I moved back from Aurora to Firefox 20.0. Same goes for running both versions in safe mode. It also persists on every website, from Google to anything else.
Does anyone else experience this issue?

---

### Post by QIII on 2013-04-18
*Moved to **Ubuntu +1***

---

### Post by zika on 2013-04-19
Dod You try to change nglayout.initialpaint.delay in about:config?
[http://kb.mozillazine.org/Nglayout.initialpaint.delay](http://kb.mozillazine.org/Nglayout.initialpaint.delay)

---

### Post by IdoSC on 2013-04-19
> **zika said:**
> Dod You try to change nglayout.initialpaint.delay in about:config?
[http://kb.mozillazine.org/Nglayout.initialpaint.delay](http://kb.mozillazine.org/Nglayout.initialpaint.delay)
Nope, in fact searching for that variable in about:config returns zero results.

---

### Post by zika on 2013-04-19
> **IdoSC said:**
> Nope, in fact searching for that variable in about:config returns zero results.It does not exist by default...
Also, take a look at pipelining...

---

### Post by serdotlinecho on 2013-04-19
Have you tried delete your .mozilla folder and have fresh/default state?

---

### Post by zika on 2013-04-19
> **serdotlinecho said:**
> Have you tried delete your .mozilla folder and have fresh/default state?There is no more need for brute force methods... Just visit about:support page...

---

