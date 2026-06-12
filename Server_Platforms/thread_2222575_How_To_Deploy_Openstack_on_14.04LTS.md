---
title: "How To Deploy Openstack on 14.04LTS"
date: 2014-05-07
forum: Server Platforms
---

### Post by ian44 on 2014-05-07
Hi All,

I've been following the official Ubuntu guide for deploying Openstack ([http://www.ubuntu.com/download/cloud/install-ubuntu-cloud](http://www.ubuntu.com/download/cloud/install-ubuntu-cloud)) and have found it quite difficult.  There are a lot of holes and omissions in the documentation.  For example step 7 "Deploy Ubuntu OpenStack using Juju." has no reference to Openstack and talks about generally deploying charms with Juju (not helpful). 

Has anyone successfully deployed Openstack on Ubuntu using MAAS and Juju and if so do you have a link to a good guide?  At the moment I'm looking at Packstack (RHEL) or doing it all by hand with [http://docs.openstack.org/trunk/install-guide/install/apt/content/](http://docs.openstack.org/trunk/install-guide/install/apt/content/) 

Any help would be much appreciated. 

Thanks

---

### Post by Gyokuro on 2014-05-07
Hi Sure as they want that you  use Juju and whatever but I suggest you go with the guide from openstack for Ubuntu and they are (openstack community) really helpful. Another thing is in case you want to switch later the distribution  (Ubuntu => Debian) for some reason it's easier to do this migration due to fewer distribution "addons". However you have to learn and live OpenStack and it's somehow complicated that you can not go in production within a day. For a fast result Ubuntu Cloud and Juju is more suited.  However if you want to go the route via JuJu take a look at the documentation: [https://juju.ubuntu.com/](https://juju.ubuntu.com/)  Oh and maybe you should try both ways and decide later which one is easier and more comfortable  or suited for your environment and check the Ubuntu Cloud and Juju forum.

---

