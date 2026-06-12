---
title: "Apport no longer catching an application crash"
date: 2012-03-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by WebDrake on 2012-03-10
I've been having continuous problems with an application (Frescobaldi) crashing when trying to open files.  The bug report is here:
[https://bugs.launchpad.net/ubuntu/+source/frescobaldi/+bug/939196](https://bugs.launchpad.net/ubuntu/+source/frescobaldi/+bug/939196)

... and a corresponding GitHub discussion is here:
[https://github.com/wbsoft/frescobaldi/issues/33](https://github.com/wbsoft/frescobaldi/issues/33)

As per the developer's request I have tried installing the various -dbg packages necessary to generate a more informative stacktrace.  However, Apport is now no longer catching the crash -- the program simply goes down and Apport does not respond.

Uninstalling the -dbg packages again has made no difference to Apport's (lack of) response.

On an immediately previous crash, I deselected the "send information to Launchpad" tickbox in Apport, as I'd already created the bug report.  Could this be responsible?  If so, how do I tweak Apport to start tracking the application's crashes again?

Thanks in advance for any advice!

---

