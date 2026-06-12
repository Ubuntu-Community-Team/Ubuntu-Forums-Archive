---
title: "Configuring OpenStack on Ubuntu 12.10"
date: 2012-11-28
forum: Ubuntu Cloud and Juju
---

### Post by Ulibuntu on 2012-11-28
Hi to all.
I downloaded and installed Ubuntu server 12.10. I'm looking for a guide in order to start the OpenStack installation and/or configuration.
Which procedure do I follow?

---

### Post by castrojo on 2012-12-08
Hey!

The Ubuntu/Openstack instructions are available here:

[https://help.ubuntu.com/community/UbuntuCloudInfrastructure](https://help.ubuntu.com/community/UbuntuCloudInfrastructure)

It's a complicated beast though, I recommend hopping onto IRC if you have issues, join #ubuntu-server and we can work on helping you work through it.

---

### Post by mojorising on 2013-03-11
Here are some instructions for any Googlers that arrive here like I did. 

[https://github.com/mseknibilel/OpenStack-Folsom-Install-guide/blob/master/OpenStack_Folsom_Install_Guide_WebVersion.rst](https://github.com/mseknibilel/OpenStack-Folsom-Install-guide/blob/master/OpenStack_Folsom_Install_Guide_WebVersion.rst)

This set is specifically for version 12.10 of Ubuntu and works for two or more servers (one control node and one compute node). The official OpenStack documents at [http://docs.openstack.org/trunk/openstack-compute/install/apt/content/](http://docs.openstack.org/trunk/openstack-compute/install/apt/content/) have a similar aim but are not as concise and they are for version 12.04 LTS of Ubuntu. 

If you just want to take this all for a test drive on a single server, I highly recommend Devstack ([http://devstack.org/](http://devstack.org/)). I have tried a few different methods for that in the past and the Devstack scripts have definitely been the best way to go in my experience. 


Have fun,
Mike

---

