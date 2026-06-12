---
title: "Server kernel boot parm no longer working."
date: 2011-08-21
forum: Server Platforms
---

### Post by MAFoElffen on 2011-08-21
I brought this up in development tests of Server 11.04 dev versions that the linux kernel parameter of apm=off or noapm stopped working in the server kernels.  What it should do is keep the monitor from going blank after the 10 minute default.  It worked up through  server versions to 10.10, then stopped working.  It didn't seem to affect Desktop versioned kernels.

After 6-8 months later and now through testing for 11.10 dev version desktop and server editions, this omission still exists, without finding any alternate methods or workarounds...

If anyone is interested, has any comments or would like to add support in that it also affects them, I submitted this bug report on this:

[Ubuntu Bug #829846 - linux kernel parm apm=off or noapm not working]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/829846")

---

