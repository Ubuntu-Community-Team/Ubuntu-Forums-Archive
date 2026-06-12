---
title: "dpkg stalling"
date: 2012-08-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jfernyhough on 2012-08-28
Argh...

Trying to do some updates using synaptic and it stalled while installing libcups(something). So I Ctrl-C and $ sudo dpkg --configure -a to finish it up.

Then I try again, Synaptic stalls and no longer responds to Ctrl-C. This time I xkill, $ sudo rm /var/lib/dpkg/lock and again try a $ sudo dpkg --configure -a. Now dpkg has stalled part way through the "Setting up... ", won't respond to ctrl-c, won't respond to a $ sudo pkill dpkg (which itself doesn't complete).

Also a $ ps ux doesn't complete. This isn't good. Hmm...

I'm not looking forward to trying a restart, I'm not sure the system will come back up again.

---

### Post by jfernyhough on 2012-08-28
OK, so I guess I'll put that down to a solar flare or local EMP.

Restarted, went to a terminal, did 
$ sudo dpkg --configure -a
then a
$ sudo apt-get install -f
and everything is fine again (or appears to be ;)).

Weird.

Might have been the -12 kernel, or might have been preload (which I installed then uninstalled).

---

