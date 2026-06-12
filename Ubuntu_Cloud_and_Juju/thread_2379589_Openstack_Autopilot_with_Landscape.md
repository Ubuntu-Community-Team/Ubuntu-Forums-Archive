---
title: "Openstack Autopilot with Landscape"
date: 2017-12-07
forum: Ubuntu Cloud and Juju
---

### Post by e.ms on 2017-12-07
Is there currently a way to install Ubuntu Openstack with Landscape?

We tested the installation with the two images (16.04.3, 17.10).
We have followed the installation instructions from the following links.

***1. [https://www.ubuntu.com/download/cloud/build-openstack](https://www.ubuntu.com/download/cloud/build-openstack)***[FONT=&quot][/FONT]
     [FONT=&quot][/FONT][FONT=&quot][/FONT]
we start conjure-up (sudo snap install conjure-up --classic)
Landscape is not displayed under other


***2. [https://insights.ubuntu.com/2014/11/06/putting-your-openstack-on-autopilot/](https://insights.ubuntu.com/2014/11/06/putting-your-openstack-on-autopilot/)***[FONT=&quot]

[/FONT]**sudo add-apt-repository ppa:cloud-installer/stable**
> Cannot add PPA: 'ppa:~cloud-installer/ubuntu/stable'.
The team named '~cloud-installer' has no PPA named 'ubuntu/stable'
Please choose from the following available PPAs:
* 'simplestreams-testing':  Simplestreams Changes Testing 
 
**sudo apt install openstack**
> Package openstack can not be found

can someone help me with this?
The MAAS server is installed and is working. The OpenStack installation with Landscape does not work.

---

