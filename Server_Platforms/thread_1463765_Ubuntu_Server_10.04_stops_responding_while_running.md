---
title: "Ubuntu Server 10.04 stops responding while running X11 application remotely"
date: 2010-04-27
forum: Server Platforms
---

### Post by Aaron44126 on 2010-04-27
Hi all,

I installed Ubuntu Server 10.04 RC on a new machine a few days back.  While working to get it set up, a couple of times, I've been running an X11 application remotely (via SSH) and the machine stops responding over the network.

When this happens...
 * All ssh sessions (and any other connections) are terminated.
 * No new ssh sessions (or any other connections) can be created.
 * You can't ping the machine.

... but the machine is still running, you can see disk activity, and you can use it from a directly attached monitor/keyboard fine.

I'm not completely sure that X11 has anything to do with the picture, but both times this has happened, I've had a remote X11 window open.

Any ideas why this may be happening and how to recover from this situation without rebooting?  Things to check if/when it happens again?  Thanks.

---

