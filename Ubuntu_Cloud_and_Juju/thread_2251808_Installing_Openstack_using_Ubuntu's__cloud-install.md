---
title: "Installing Openstack using Ubuntu's  cloud-installer"
date: 2014-11-06
forum: Ubuntu Cloud and Juju
---

### Post by bmullan2 on 2014-11-06
Ubuntu engineers have been busy building a great **new OpenStack cloud-installer** capability that *utilizes Juju, LXC, KVM, MAAS* together in a very cool new deployment of Openstack "services" (Horizon, Swift, Neutron etc).

Most Openstack deployments are strickly hardware virtualized VM's (KVM, VMware etc).    And most dedicate either an entire bare metal machine or an individual VM to each Openstack "service".

Of course that works but it is not an optimal way to utilize servers.

Ubuntu's cloud-installer presents you with a menu where you can select to do a **Single-Installer **or **Multi-Installer **deployment.

Single-Installer will deploy all of Openstack to you laptop or PC (minimum recommended HW = 8 Core, 12G ram, 100GB HD)
This will utilize only 2 (or 3) KVM VM's and deploy all of the Openstack "services" into LXC containers inside those KVM VMs.
Installation on my i7 32G ram laptop takes about 2.5 hours.

Multi-Installer utilizes Canonical's MAAS in addition to all of the above but it is targeted to more real-world deployment in a DataCenter versus the private Openstack cloud for learning that the Single-Installer gives you.

You can find more information on the Cloud-Installer GITHUB page:

[https://github.com/Ubuntu-Solutions-Engineering/openstack-installer](https://github.com/Ubuntu-Solutions-Engineering/openstack-installer)

---

### Post by chris240 on 2014-11-12
Well i tried this Multi-Installer and work well

[http://www.ubuntu.com/download/cloud/install-ubuntu-openstack](http://www.ubuntu.com/download/cloud/install-ubuntu-openstack)

---

### Post by KaMZaTa on 2015-04-11
> **chris240 said:**
> Well i tried this Multi-Installer and work well

[http://www.ubuntu.com/download/cloud/install-ubuntu-openstack](http://www.ubuntu.com/download/cloud/install-ubuntu-openstack)

*"Installing Ubuntu OpenStack requires at least seven machines with two disks, two of which have two network interfaces..."*

I'm just looking for installation info about OpenStack (I haven't try to install yet) to create my own private cloud. I'ld like to create a scalable infrastructure with the ability, in the future, to add nodes to use for high availability.

How many machines do I need? **At least 7**? Is it right? What about system backups?

---

### Post by vince-vlara on 2015-04-23
I got excited by the prospect of using Canonical's tools to setup my OpenStack. However, this soon turned to disappointment when I started looking for documentation. I am really frustrated by the lack of detailed information regarding preparation. I have ten servers available but no idea if they are suitable for an Ubuntu OpenStack Multi-Install.

Why two disks? 
-Is one for the OS? If so, what is the minimum size required?
-Is one for OpenStack? If so, what is the minimum size required? 
-Do they need to be the same size and type for software mirroring?
Why is there no diagram showing the hosts, their functions and the network cabling required?
Why is there no list of minimum system requirements for each host?
Which network or host needs a connection to the internet gateway?
Can the networks be setup as VLANs on a single network adapter?
Which hosts must have hardware virtualization capable CPUs?
Can any of this be run on 32-bit or is it all 64-bit only?

Can anyone answer these questions for me? Is there a secret HOW-TO somewhere?

Reading OpenStack's own documentation there is at least a diagram with minimum requirements but I have no idea what the correlation is with the seven host requirement of Ubuntu OpenStack Multi-Installer. I guess I will be going back to the original plan, building it myself using OpenStack documentation.

---

