---
title: "Using juju with autopilot to add openstack services"
date: 2016-04-12
forum: Ubuntu Cloud and Juju
---

### Post by magnus11 on 2016-04-12
I've installed the Ubuntu Autopilot Openstack ova template on an ESXI server. Everything works fine but now I would like to add new Openstack services to my installation, such as Trove. I would like to have this service integrated with my Openstack horizon dashboard. The problem is that I can't see how I can use the existing Juju that has been deployed by Autopilot?

When I download the configuration file (yaml) for Juju from the landscape panel I tried to bootstrap it. Then it created a new juju environment on my openstack cluster. Then when I install stuff through that juju instance it's just running inside my Openstack environment. So it has become some sort of "stacked" juju environment. I want to have for example Trove integrated with my Openstack dashboard and not inside some VM:s in the Openstack environment.

Any idea how I can use juju to accomplish this?

---

### Post by Gary_Haegens on 2016-04-13
I am but a humble neophyte here but can't you run "openstack-status" and it brings up the install screen then select a to add services to openstack?  You should also be able to add from the Juju gui if it is installed.  Let me know if I am correct because I really am struggling myself in this "simple" environment.

---

