---
title: "error while installing openstack"
date: 2014-11-07
forum: Ubuntu Cloud and Juju
---

### Post by Malik_adil_nawaz on 2014-11-07
i want tio install
sudo apt-get install git
but an error becomes
E: apt-get unable to locate package git
then i update and upgrade through terminal command but again for this command same error faces.
kindly help
system used:
hp g6 pavilion i5
os: ubunto 14.04 also 12.04

---

### Post by TheFu on 2014-11-07
Probably a simple network setup issue.
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has troubleshooting steps to determine exactly where the problem is.

Running openstack is 100x harder than installing git.  Just sayin'.

---

### Post by TheFu on 2014-11-07
forum double post bug.

---

### Post by chris240 on 2014-11-12
Or Try this installation works well

[http://www.ubuntu.com/download/cloud/install-ubuntu-openstack](http://www.ubuntu.com/download/cloud/install-ubuntu-openstack)

---

### Post by TheFu on 2014-11-12
> **chris240 said:**
> Or Try this installation works well

[http://www.ubuntu.com/download/cloud/install-ubuntu-openstack](http://www.ubuntu.com/download/cloud/install-ubuntu-openstack)

Hard to use Landscape in a lab that doesn't have internet connectivity or budget, isn't it?

---

### Post by chris240 on 2014-11-13
well in that installation there is landscape single or multi-install

---

### Post by alittlek on 2014-11-13
> **chris240 said:**
> Or Try this installation works well

[http://www.ubuntu.com/download/cloud/install-ubuntu-openstack](http://www.ubuntu.com/download/cloud/install-ubuntu-openstack)


I'm also going that way (option: Landscape install) but get stuck after commission nodes:
They are all in ready state (5 nodes with 2 disks and all with two nic's) but no node get enlisted in landscape nor https://<server>/account/standalone/openstack/create-cloud recognizes any node.

Any hints?

---

