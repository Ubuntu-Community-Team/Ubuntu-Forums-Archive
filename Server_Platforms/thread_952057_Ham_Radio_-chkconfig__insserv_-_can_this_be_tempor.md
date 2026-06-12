---
title: "Ham Radio -chkconfig / insserv - can this be temporarily changed"
date: 2008-10-18
forum: Server Platforms
---

### Post by frank754 on 2008-10-18
I've been playing around with some Ham Radio apps and this particular suite, QTel, aims to be a Linux version of Echolink. I have managed to get the client portion installed using alien (as the app was written for Fedora Core). The server portion needs to dig its claws into init.d, etc., and upon install it first complained about missing chkconfig. This part I was able to rectify. But now it's looking for insserv (I'm using Hardy Heron). When I go to install insserv with apt-get, this is what appears, which does not look good:

The following packages will be REMOVED:
  apparmor apparmor-utils initscripts system-services ubuntu-minimal upstart-compat-sysv
The following NEW packages will be installed:
  insserv
0 upgraded, 1 newly installed, 6 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 52.4kB of archives.
After this operation, 4342kB disk space will be freed.
Do you want to continue [Y/n]? n

I have read that messing with insserv will hose the system upon reboot. But can I install this temporarily, then finish installing my radio app so it gets into the init system as it wishes, and then do the reverse of what apt-get proposes above (i.e.) restore the other apps again manually & delete insserv?

---

