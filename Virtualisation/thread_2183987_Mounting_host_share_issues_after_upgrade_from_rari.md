---
title: "Mounting host share issues after upgrade from raring to saucy"
date: 2013-10-27
forum: Virtualisation
---

### Post by twinturbotom on 2013-10-27
All,

I recently upgraded an ubuntu server running in a virtualbox vm from raring to saucy.  Right after the upgrade my system would ask me to hit "S" to skip the loading of shares mounted in my /etc/fstab.  After skipping these mounts I was able to manually mount them.  I've played with options like "nobootwait" that appear to enable booting without having to hit "S" but I still have to manually mount the shares.  This isn't my main concern.  After uninstalling and reinstalling virtualbox-guest-additions I am unable to "ls" into these mounted shares.

strace ls reveals: getdents(3, /* 1 entries */, 32768)     = 32

Several virtualbox forum posts and google research like this [forum post]("https://bbs.archlinux.org/viewtopic.php?pid=1326554") show others have experienced this with the only solution that works for some is to patch virtualbox or downgrade kernel.  Patching vbox may be beyond my capabilities and would require step by step instruction.
Any thoughts on how I can regain my virtualbox mounted shares?

Thank you for your help.

---

