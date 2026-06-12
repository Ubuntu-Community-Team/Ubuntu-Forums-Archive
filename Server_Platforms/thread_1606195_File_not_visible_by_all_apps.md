---
title: "File not visible by all apps"
date: 2010-10-26
forum: Server Platforms
---

### Post by dargaud on 2010-10-26
Hello all,
ok, this is a strange problem that is probably not related to Ubuntu but more to the filesystem.

I have an app that creates a file and adds to it regularly (without closing it). I can see the file with 'ls' immediately. But another app with an oldish X11 user interface doesn't show the file in its [Open] dialog for several minutes (it does some kind of 'tail -f'). There are several megs copied to the file every minute, so it can't be a simple buffer not yet flushed.

Any idea how to make this file visible by all apps ?!?
Thanks

---

