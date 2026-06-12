---
title: "git downgrades my kernel"
date: 2008-07-01
forum: Repositories &amp; Backports
---

### Post by LK.Atwork on 2008-07-01
Hi

I'm trying to build linux-2.6.26-rc7 with unionfs support.

I downloaded linux-2.6.26-rc7.tar.bz2 and untarred it. I then cd'd to the untarred directory and did:

git-init
git add .
git pull git://git.kernel.org/pub/scm/linux/kernel/git/ezk/unionfs.git

Although unionsfs was pulled down, my linux dropped from linux-2.6.26-rc7 to linux-2.6.26-rc1. Is there a way that I can avoid this downgrade to rc1?

thanks for your help
LK

ps: I had posted this to the wrong group earlier :-(

---

