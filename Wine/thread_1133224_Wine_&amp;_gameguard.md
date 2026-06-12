---
title: "Wine &amp; gameguard"
date: 2009-04-22
forum: Wine
---

### Post by h4mx0r on 2009-04-22
[http://www.winehq.org/docs/winedev-guide/threading](http://www.winehq.org/docs/winedev-guide/threading)

That is the reason that gameguard and similar apps do not work under wine. It is because of the difference in threading for win32 and linux systems. Some also mentioned in a long debated ubuntu forum that glib is a cause of failure.

However if recompiled wine can use either kthread or pthread. It seems kthreads is the older method that doesn't support nptl and uses a subset of a hacked pthread inside of wine to emulate such complex threading of a win32 environment. Could that possibly pose a fix?

It is also an interesting note in this article "On non-Linux systems the threading interface is typically not powerful enough to replicate the semantics Win32 applications expect and so kthreads with the pthread overrides are used." so don't know if this fix would work on the mac port of wine.

---

### Post by coldReactive on 2009-04-22
Just use games that don't use gameguard. Like the IGG Games. :D

/sarcasm

---

### Post by h4mx0r on 2009-04-22
I just find it rather insulting that there is anything wine is not considered "capable" of doing.

---

### Post by coldReactive on 2009-04-22
> **h4mx0r said:**
> I just find it rather insulting that there is anything wine is not considered "capable" of doing.

I find it also insulting that AVG shuts itself off when gameguard runs.

---

### Post by NightMKoder on 2009-04-23
Wine's threading is not the problem (in fact the problem you speak of was fixed....a looong time ago (Dec 2003, kernel 2.6 release)). gameguard won't work on wine because it (illegally) installs hidden device drivers on windows, and wine does not support device drivers (this would probably require switching to privileged mode, which wine will not do).

In short - don't expect gameguard to work on wine anytime soon.

---

### Post by cogadh on 2009-04-23
We do have a [sticky on this very subject]("http://ubuntuforums.org/showthread.php?t=1069960") at the top of the forums.

---

