---
title: "OpenStack for a personal Cloud"
date: 2013-11-26
forum: Virtualisation
---

### Post by taylorjonl on 2013-11-26
I am looking to get some advice from some experts before a go down a bad path.  I am trying to setup a home server that will be used for my personal cloud.  Here are the parts:


Tyan S7012GM4NR 
2.4ghz Quad Core Xeon
12GB 1066MHZ DDR3 ECC
Areca ARC-1680IX-24 Raid Card
115GB Vertex 3 SSD
20x 2TB Seagate HDD


This system has room to grow, I have plans to get another CPU and from 12GB to 36GB depending on needs.


I am trying to build a system that can host the various services I want to run.  Initially I am trying to get a development environment up for a cloud(small cloud, just my house) that will be used for some home automation using the BeagleBone ARM board as a node, so my first requirement is being able to spin up a new node in my development environment.  The nodes would be linux running some software to support a REST API at first then may be progressing into a HTTP GUI.


Later I want to move my HTPC under this beast, this will require PCI pass-through for my Ceton InfiniTV card.


My initial thought was to install OpenStack, but is this too much?  I am reading that they recommend 2 or 3 or more nodes, I don't want to have many other computers running in my house after this box is running.  It seems very simple to spin up new instances in OpenStack.


Other options I have looked at Xen, KVM and Qemu.  I have poked around with Xen and it seems pretty cool, lots harder to use than OpenStack which means more time spent spinning up instances and not on developing software.  I know that Xen can be used with OpenStack as a Compute node but I see that there are other parts they recommend offloading, like Keystone(identity), Glance(image storage), Cinder(block storage), Neutron(networking).


Post has some decent details on the pieces:


[https://ask.openstack.org/en/question/5185/what-are-the-minimum-hardware-requirements-of-openstack/](https://ask.openstack.org/en/question/5185/what-are-the-minimum-hardware-requirements-of-openstack/)


I know in Xen you have Dom0, you normally don't install stuff in Dom0, right?  Do all the pieces(identity, image storage, block storage and networking) go into Dom0?


Any input is appreciated...

---

### Post by TheFu on 2014-10-04
So  - I see this thread is really old. 

Hopefully you've discovered that opencloud is NOT meant for home users. If you intend to have fewer than 50 VMs and at least 3 physical systems, opencloud is overkill.  Opencloud runs on top of Xen or KVM or LXC or ...  Any upgrades are painful to Opencloud - this is meant for businesses with professional IT people doing this full-time, not home hobbyists.  Perhaps someday ... in 5-10 yrs.

PCI passthru means you probably want Xen. It is more mature there. KVM should work too - I just haven't tried/needed it.

BTW - your current system is already HUGE for what any home should need - unless you run lots of Windows systems.  I run a Core i5 w/ 16G and have 15 VMs on it with headroom, including a Windows7 Media Center with 4 network tuners. Network tuners make putting it into a VM almost trivial. Oh - and I use KVM - dumped Xen (after 4 yrs running it) due to patch surprises preventing the entire system from booting. This was a business need, couldn't have that. Things are probably better now - never had any issues with KVM. Extremely stable, fast, easy to manage with libvirt font-ends.

Sounds to me like you may want something like proxmox - instead.

Would love to hear what you decided was the best answer and how things are going.

---

