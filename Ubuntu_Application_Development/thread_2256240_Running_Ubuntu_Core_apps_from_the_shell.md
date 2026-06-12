---
title: "Running Ubuntu Core apps from the shell"
date: 2014-12-10
forum: Ubuntu Application Development
---

### Post by duncan_bayne on 2014-12-10
Hi,

I'm investigating the use of Ubuntu Core for packaging apps, and I have a question about composability and command-line use.

Imagine I have two Core apps, AppA and AppB.  From the shell, I'd like to cat a file from somewhere under $HOME, pipe it into AppA.binary, pipe the output into AppB.binary, and then redirect the output into a file elsewhere under $HOME.

Presumably, to do this, the shell must be running from something *other* than a Core app, that is, something with write access to my entire home directory?  Or is the plan to (eventually) distribute shells as Core apps with broader permissions than regular core apps?

My worry is that Core might lead to the sort of siloing that, while desirable in some ways from a security perspective, might make casual programming and advanced shell use difficult.

Yours,
Duncan Bayne

---

