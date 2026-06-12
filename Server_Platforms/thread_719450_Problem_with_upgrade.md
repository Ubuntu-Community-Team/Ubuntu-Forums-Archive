---
title: "Problem with upgrade"
date: 2008-03-09
forum: Server Platforms
---

### Post by Milambar on 2008-03-09
I am trying to upgrade my server with:
sudo do-release-upgrade

And I must say that  I'm quite disheartened with the whole proceedure. I have a lot of work on the machine so I cannot wipe and reinstall afresh (and I shouldn't have to, this is Linux, not Windows).

The above command downloaded nearly 1GB of files, and then started installing them. However it sometimes quits out with a dependency error (WTF? This is an apt-get system, nor an rpm system!). In itself this is no huge problem, fix the dependency error, and restart the upgrade...

Only, it restarts from the beginning. Reinstalling what its already installed. This is seriously suboptimal, and its been going for 2 (yes 2) days now because of this.

Is there any way to make the installer (apt-get upgrade) pick up at the point where the error occurred, rather than at the very beginning again?

---

### Post by Sef on 2008-03-09
Moved to Server Platform.

---

