---
title: "starting (and respawning) monit on Ubuntu hardy"
date: 2008-09-18
forum: Server Platforms
---

### Post by stankaufman on 2008-09-18
What is the proper way on Ubuntu hardy to get monit to launch at boot and to respawn if monit crashes?

With Debian etch, it’s easy since Debian still uses /etc/inittab — but Ubuntu has abandoned this in favor of upstart and configs to be made (apparently) in /etc/default and maybe /etc/event. This discussion ([http://www.ubuntugeek.com/monitoring-ubuntu-services-using-monit.html](http://www.ubuntugeek.com/monitoring-ubuntu-services-using-monit.html))  says that simply setting startup=1 in /etc/default/monit will cause monit to start, but this appears not to be the case. This writeup says nothing about using update-rc.d to install links in the various runlevel directories.

I’ve compiled and installed monit 4.10.1 (the latest stable version), and it runs fine from the command line (sudo /etc/init.d/monit start). However, when I reboot, monit does not start — unless I add the update-rc.d links. Was this step simply missing from the above otherwise authoritative-sounding writeup?

Even if the update-rc.d step should be used to launch monit at boot, what about respawning monit? The inittab approach restarts monit if it dies for some reason. What is the Ubuntu Way to accomplish this? Surely there must be a way, or is this a reason to stick with Debian? Or else what am I fundamentally not understanding here?

Many thanks in advance!

---

### Post by cariboo on 2008-09-19
The files are the configuration files from the version of monit in the repositories.

Jim

---

