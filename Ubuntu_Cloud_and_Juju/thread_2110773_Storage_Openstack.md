---
title: "Storage Openstack"
date: 2013-01-31
forum: Ubuntu Cloud and Juju
---

### Post by 2danny9 on 2013-01-31
Hi all,
 
I'm wondering... is it possible, to configure openstack on Ubuntu 12.04, and use it as a type of file server, i.e. it has a a few giga bytes from a machine or two, and then use these available resources to share files. It will be done over LAN and on virtual machines. 
 
I've spent some time on it and now I'm worried that when I've got it Openstack, nova, object/swift etc, up and running it would have been all in vain. 
 
Could you guys guide me.
 
I've been using the following book - OpenStack Cloud Computing Cookbook** -** to configure openstack on ubuntu server 12.04 via virtualbox on windows.
 
Thank you all in advance!
 
Danny

---

### Post by IPvFletch on 2013-02-04
The newer nova versions support NFS, just set up NFS shares on your servers and then mount them on your stack server. Then you can r/w to them as if they are a local disk. You can deploy instances to them as well by mapping your _base folder..

---

### Post by castrojo on 2013-03-03
You probably don't need full blown openstack for this, you can just use cpeh: [http://ceph.com/](http://ceph.com/)

(It's in Ubuntu already!)

---

### Post by tgalati4 on 2013-03-03
Spend some time here if you want to install a "personal cloud".   [http://devstack.org/](http://devstack.org/)  Ask Elizabeth for a copy of her talk:  [https://www.socallinuxexpo.org/scale11x/presentations/ubuntu-cloud](https://www.socallinuxexpo.org/scale11x/presentations/ubuntu-cloud).

---

