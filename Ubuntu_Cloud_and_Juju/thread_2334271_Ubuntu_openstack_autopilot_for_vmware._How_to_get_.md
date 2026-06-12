---
title: "Ubuntu openstack autopilot for vmware. How to get it to work?"
date: 2016-08-17
forum: Ubuntu Cloud and Juju
---

### Post by Silver565 on 2016-08-17
Hi Everyone,

I've had a look at this link:

[http://www.ubuntu.com/cloud/openstack/autopilot](http://www.ubuntu.com/cloud/openstack/autopilot)

The instructions seem pretty straight forward. I can't get a node to add, everything I've tried results in 'commissioning failed'. So far I've had to:


[LIST]
[*]Enable the 16.04 image as all PXE boots failed
[*]Select 16.04 as the default commissioning image
[*]Enter vmware credentials and UUID for each node(VM)
[/LIST]

^ none of that was in the instructions for some reason. What I'm stuck with now is that the VMs boot up via PXE fine and go to a login screen however they all come up as commissioning failed. Has anyone managed to get the autopilot appliance to actually work?

Thanks!

---

