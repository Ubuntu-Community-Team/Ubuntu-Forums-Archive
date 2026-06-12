---
title: "remove ubuntu-desktop from server"
date: 2007-11-28
forum: Server Platforms
---

### Post by timmay on 2007-11-28
Is it possible to remove the ubuntu-desktop from a 7.10 server to restore it back to a command line only system.

Simply doing apt-get remove ubuntu-desktop didn't do anything.

Thanks

---

### Post by HermanAB on 2007-11-28
Just change the runlevel with "init 3". Don't remove the desktop stuff, you may want it again.  Sometimes a big mess is easier to fix using  GUI and then all you need to do is run "init 5".

Cheers,

Herman

---

