---
title: "anacron echoing to console"
date: 2007-11-14
forum: Repositories &amp; Backports
---

### Post by Joshua Swink on 2007-11-14
I have a problem with the output of anacron's jobs being echoed to the console. I managed to work around Gutsy's problem of all those init scripts being echoed over the login prompt, but anacron continues to produce unwanted output there.

5 and 10 minutes after boot, the message "* Reloading system log daemon..." shows up on the console. I would like to prevent it from showing up, but not by disabling the job! I want anacron to do what it's supposed to, but not mess up the console at the same time.

I've tried various things, such as making anacron start up with its output streams redirected to /dev/null, but nothing has worked so far. It seems odd too that a daemon would start up without doing that itself.

---

### Post by Joshua Swink on 2007-11-15
Ok, found the cause:

[https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/61760](https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/61760)

A workaround is to change /etc/lsb-base-logging.sh line 23 to:

 loop=y $func "$@" || true

---

