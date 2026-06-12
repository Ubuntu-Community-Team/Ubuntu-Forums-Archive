---
title: "Openstack, Maas, JuJu... Im Confused"
date: 2013-09-27
forum: Ubuntu Cloud and Juju
---

### Post by slice16 on 2013-09-27
Hi All,

I am trying to get my head around the connection between Openstack, JuJu and Maas and have managed to confuse myself. I am hoping someone can help me out with working things out?

Basically, I understand Maas. You use it to deploy an OS image to a cluster using PXE. You can then deploy JuJu Charms to this computer resource. Nice and easy. 

I also know you can deploy the openstack charms to this compute resource provided by Maas. So I assume the openstack charms run as Virtual machines?

This is where I get confused... would you use Maas to configure your compute nodes as hypervisors and connect to nova? Or would you simply deploy open stack to Maas, and then have separate infrastructure for your hypervisor stack?

Thanks

Paul

---

