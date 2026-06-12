---
title: "cannot encrypt files with seahorse-nautilus"
date: 2013-09-08
forum: Ubuntu Development Version
---

### Post by mc4man on 2013-09-08
At least here nothing happens, just an extended warning - 
> ** (seahorse-tool:14708): WARNING **: couldn't load all the keys (1/2) from GPGME

(seahorse-tool:14708): GLib-WARNING **: GChildWatchSource: Exit status of a child process was requested but ECHILD was received by waitpid(). Most likely the process is ignoring SIGCHLD, or some other thread is invoking waitpid() with a nonpositive first argument; either behavior can break applications that use g_child_watch_add()/g_spawn_sync() either directly or indirectly.

[https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/1222538](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/1222538)

fixed with small patch to seahorse-nautilus

---

