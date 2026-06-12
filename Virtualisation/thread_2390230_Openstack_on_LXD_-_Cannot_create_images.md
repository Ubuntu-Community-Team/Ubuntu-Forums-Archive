---
title: "Openstack on LXD - Cannot create images"
date: 2018-04-26
forum: Virtualisation
---

### Post by quartzeye on 2018-04-26
Not sure what is going on but every image I try to import, ultimately gets stuck in a "queued" status.  I have tried to import using Horizon and from the CLI.  I have the images on the Host with 777 permissions.  The import never completes and I get a 500 error from the glance image service on the CLI.  However, glance seems to be running.

I suspect it might have something to do with the mysql database but I cannot check it as the conjure-up install seems to create encrypted passwords that I cannot seen to get to them so that I can log onto the mysql instance and check the db config.  Not a lot of info out there on how to debug this but I think something in the install from Ubuntu isn't quite complete.

Any pointers would be helpful.  I have been banging my head around getting a working environment for weeks.  I hope I don't have to drop back and rebuild this entire thing again for the umpteenth time.  Trying to learn how to use openstack instead becoming an openstack install guru.

---

