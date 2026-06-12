---
title: "Compile from source vs. repositories"
date: 2006-01-28
forum: Server Platforms
---

### Post by faulkner132 on 2006-01-28
From a server standpoint, what is the difference?  Simple example being running Apache, MySQL, and PHP by downloading the latest from the respective sites and installing versus installing the older versions in the repositories.  Are there speed / stability / security issues with doing one over the other?

I'm sure this has been answered already, if so, please point me to the thread... my searches haven't come up with much.

Thanks.

---

### Post by LordHunter317 on 2006-01-29
[QUOTE=faulkner132]From a server standpoint, what is the difference?[/quote]Compiling from source unless absoultely necessary is a waste of time, and normally results in a inferior product. I don't have the time the package maintainer due to build software, and apply patches nor the ability to test as wide a range of configurations.

>  Are there speed / stability / security issues with doing one over the other?In the majority of cases, source compiled packages will likely be slower, less stable, and less secure.  Most software you use is reasonably heavily patched.

Even if the cases where none of those apply, it's usually more difficult to use.

---

### Post by towsonu2003 on 2006-01-29
security: you won't have to be subscribed to the mailing list of the code maintainer (to be made aware of all updates) and recompile everytime the source code is updated by its maintainer if you use repos. well, uhm, ok, you'll still have to be subscribed to some security mailing list to know about the exploits ;)

---

### Post by faulkner132 on 2006-01-29
I see, very good advice.  So the Ubuntu dev team does modify certain packages for Ubuntu-specific security and stability?

Looks like I the repos are always the way to go.

---

### Post by az on 2006-01-29
[QUOTE=faulkner132]I see, very good advice.  So the Ubuntu dev team does modify certain packages for Ubuntu-specific security and stability?
[/QUOTE]

More like modifications and small additions to integrate with other distro-specific functionalitites (menu entries for certain desktop applications are one example of this)

---

