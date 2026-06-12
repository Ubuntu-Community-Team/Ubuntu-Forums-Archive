---
title: "restart service at startup"
date: 2012-05-13
forum: Server Platforms
---

### Post by mons00n on 2012-05-13
What would be the best way to go about restarting a service when my server is restarted?  I'm having issues with mumble-server on 12.04x64 starting with the computer ([see this thread for details]("http://ubuntuforums.org/showthread.php?t=1975872")).  I filed a bug report on launchpad but don't have much hope in getting it resolved any time soon.  I can't even seem to find anyone else having the same problem so I'm not sure if it's isolated.

Basically if I run 'sudo /etc/init.d/mumble-server restart' the mumble server starts working properly...I'd like to have this happen automatically.  I saw some posts saying the best way to have something execute on startup is to put a script in /etc/rc.local, or possibly in /etc/network/if-up.d - but I have no idea what the best option would be.  Any tips would be greatly appreciated.  Thanks!

---

### Post by maverickaddicted on 2012-05-16
I think the best option is to add the script in /etc/rc.local. If you want you can read about the Ubuntu boot process to get more ideas. Here is the link -

[http://manpages.ubuntu.com/manpages/lucid/man7/boot.7.html](http://manpages.ubuntu.com/manpages/lucid/man7/boot.7.html)

---

