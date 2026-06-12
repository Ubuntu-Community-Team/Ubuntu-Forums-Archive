---
title: "Suspending to RAM after period of inactivity and resuming for scheduled recordings."
date: 2017-04-21
forum: Server Platforms
---

### Post by elsmandino2 on 2017-04-21
Hi,

I have just set up a new server based upon Ubuntu Server 16.04 LTS.

I have installed TVHeadend on it to do all my TV recording.

The server is pretty much used constantly from about 6pm to about 1am, when it is either recording TV or streaming video to clients.

Other than this period, it doesn't do much but idle so I was hoping to try and find a way of having it suspend to RAM during periods of inactivity.

Because of the risk of a recording being scheduled between 1am and 6pm, the server has to be able to resume from suspend for scheduled recordings.

I have stumbled across this, which appears to be offering exactly what I am after:

[https://github.com/git-developer/autosuspend](https://github.com/git-developer/autosuspend)

The author confirms that it works on their Debian server.

What (if any) changes am I going to have to make to get it working on Ubuntu Server?

---

