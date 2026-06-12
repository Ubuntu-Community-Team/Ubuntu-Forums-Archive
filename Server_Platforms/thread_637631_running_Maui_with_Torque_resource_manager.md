---
title: "running Maui with Torque resource manager"
date: 2007-12-11
forum: Server Platforms
---

### Post by osaka_dude on 2007-12-11
hello, im a Ubuntu newbie.
I ve been trying to install a resource manager (Torque) and a cluster scheduler(maui)
After a lot of work,I ve succeeded in the "make install" for both,but now im lost about how to run these together.
any ideas?

---

### Post by meatpan on 2007-12-11
During the make process for maui, did you specify the torque installation direcotry?  I believe this is the '--with-pbs' flag.

I came across a decent guide from the gentoo folks:  [http://gentoo-wiki.com/HOWTO_Torque/Maui_-_grid_scheduler_and_resource_manager](http://gentoo-wiki.com/HOWTO_Torque/Maui_-_grid_scheduler_and_resource_manager)

It shouldn't be too much different from a ubuntu install, since both distros require a hand configuration.  Keep in mind that you will need to manually set your environment variables (gentoo has some helper scripts for this).

Does this help?

---

