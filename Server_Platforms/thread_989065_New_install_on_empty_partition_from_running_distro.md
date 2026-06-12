---
title: "New install on empty partition from running distro"
date: 2008-11-21
forum: Server Platforms
---

### Post by jackocleebrown on 2008-11-21
I have a couple of small servers which I want to upgrade to more recent versions of Ubuntu. At the moment they are running 7.04 and I need some new packages which are only available on newer releases.

Rather than have the disturbance of a standard upgrade or reinstall I was wondering if it is possible to install a new version of Ubuntu on an empty partition on the machine while running the servers normally on their current versions of Ubuntu. This would mean that I can install the new systems and then restart to the new version with minimal downtime. I could also potentially get a lot of the config files in place before restarting too.

Has anyone done this?

Thanks,
Jack.

---

### Post by Philio on 2008-11-21
I guess if you were to mount the installation disk under the current OS and run the install scripts it could work.

Why don't you just do an upgrade? It takes a few mins and the only downtime will be a reboot into your new kernel.

[http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Servers%20(Recommended](http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Servers%20(Recommended))

---

### Post by jackocleebrown on 2008-11-21
Is it sensible to run an upgrade while people are accessing the box over ssh and nx (nomachine)? I would have thought that this would cause some problems.
Good suggestion with the install disk. I might have a look at that.
That would also mean that I can easily jump a version (or two)

Thanks.

---

