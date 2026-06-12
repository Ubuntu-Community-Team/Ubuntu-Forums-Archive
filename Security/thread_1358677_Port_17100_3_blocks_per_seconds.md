---
title: "Port 17100 3 blocks per seconds"
date: 2009-12-18
forum: Security
---

### Post by mrnotsure on 2009-12-18
This just started happening randomly its showing up on firestarter with several hostnames/ip adresses.

Any help?

I googled for 10 minutes

---

### Post by lovinglinux on 2009-12-18
It's blocked, so why bother. Besides, if you are not running a server listening to that port, then those connections will be rejected even if you don't have a firewall running. In fact, you probably don't even need a firewall. I would explain that, but there are [tons of threads about this subject](http://www.google.com/search?q=do+I+need+a+firewall+site%3Aubuntuforums.org).

Please read [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421) tutorial.

Those hits are probably ghost packets from a closed BitTorrent connection or something like that. 

See these:

[http://ubuntuforums.org/showthread.php?t=1176946](http://ubuntuforums.org/showthread.php?t=1176946)
[http://ubuntuforums.org/showthread.php?t=1195242](http://ubuntuforums.org/showthread.php?t=1195242)
[http://ubuntuforums.org/showthread.php?t=1112089](http://ubuntuforums.org/showthread.php?t=1112089)

If you really want to use a firewall, aside from the fact that you probably don't need it, then purge firestarter, install [gufw](apt:gufw) and forget about monitoring hits. That is just a waste of time.

Gufw is the default firewall manager now (which is just a gui for ufw, which is installed by default) and Firestarter is not recommended anymore. Lots of threads about this too.

---

