---
title: "Mythtv and apt-pinning"
date: 2005-06-12
forum: Ubuntu Backports
---

### Post by EdMcMan on 2005-06-12
Hi everyone.  I am new to the forums.  I've been using the backports and they are great.  It's a shame that ubuntu doesn't have continously updated desktop software, but I suppose it doesn't matter with a great project such as this.

Anyway, here is my problem.  I am setting up a box to be a PVR.  I installed ubuntu and copied my apt settings from my other boxes.  A newer version of mythtv is included with the backports.  However, the various plugins are not.  The older version of the plugins (not in backports) do not work with the backports mythtv.

Now, if the plugins were backported that would fix the problem.

But otherwise, I have been trying to pin the backport versions of mythtv to not install (without any success!)  I don't have the box in question plugged in right now, but I was trying something like this:

```

Package: mythtv*
Pin: version *ubp1
Pin-Priority: -1
```

That didn't seem to work.  Is there any way to pin certain backports?

Thanks  :grin:

---

### Post by Mez on 2005-06-12
try it without the * at the end of mythtv... if not... just pin it to a certain version provided in hoary.



So either

```
Package: mythtv
Pin: version *ubp1
Pin-Priority: -1
```

or

```
Package: mythtv
Pin: version 0.17-3
Pin-Priority: 1001
```

---

